---
title: '方法: エディターのファイルの種類の登録 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204120"
---
# <a name="how-to-register-editor-file-types"></a>方法: エディター ファイルの種類を登録する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディターのファイルの種類を登録する最も簡単な方法は、の一部として提供されている登録属性を使用して、 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] managed package framework (MPF) クラス。 パッケージをネイティブで実装している場合[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]、エディターなど、関連する拡張機能を登録するレジストリ スクリプトを記述することもできます。  
  
## <a name="registration-using-mpf-classes"></a>MPF クラスを使用して登録  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>MPF クラスを使用してエディター ファイルの種類を登録するには  
  
1. 提供、 <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> VSPackage のクラスで、エディターの適切なパラメーターを持つクラス。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     場所"です。Sample"はエディターで、登録されている拡張機能と、「32」は、優先順位。  
  
     `projectGuid`で定義されたその他のファイルの型の guid を<xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>します。 結果として得られるファイルはビルド プロセスの一部にならないように、その他のファイルの種類が提供されます。  
  
     `TemplateDir` 管理対象の基本的なエディターのサンプルに含まれているテンプレート ファイルを含むフォルダーを表します。  
  
     `NameResourceID` BasicEditorUI プロジェクトの Resources.h ファイルで定義され、エディターを「My エディター」として識別します。  
  
2. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドをオーバーライドします。  
  
     実装で、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドを呼び出し、<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>メソッドと次の例として、エディター ファクトリのインスタンスのパス。  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     この手順では、エディター ファクトリおよびファイルのエディター拡張機能の両方を登録します。  
  
3. エディター ファクトリの登録を解除します。  
  
     VSPackage が破棄されたときに、エディター ファクトリは自動的に登録できません。 エディターのファクトリ オブジェクトを実装する場合、<xref:System.IDisposable>インターフェイス、その`Dispose`とファクトリが登録解除された後、メソッドが呼び出された[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
## <a name="registration-using-a-registry-script"></a>レジストリ スクリプトを使用して登録  
 エディター ファクトリおよびファイルの種類を登録するネイティブ[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]は、次に示すように、windows レジストリに書き込む、レジストリ スクリプトを使用して。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>レジストリ スクリプトを使用してエディター ファイルの種類を登録するには  
  
1. レジストリ スクリプトでエディター ファクトリと定義エディター ファクトリの GUID の文字列のように、`GUID_BscEditorFactory`レジストリ スクリプトを次のセクション。 また、拡張機能およびエディター拡張機能の優先順位を定義します。  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     この例では、エディターのファイル拡張子は".rtf"として識別され、その優先順位が「50」。 GUID の文字列は、Resource.h ファイルの BscEdit サンプル プロジェクトで定義されます。  
  
2. VSPackage を登録します。  
  
3. エディター ファクトリを登録します。  
  
     エディター ファクトリに登録されている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>実装します。  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID の文字列は、Resource.h ファイルの BscEdit プロジェクトで定義されます。
