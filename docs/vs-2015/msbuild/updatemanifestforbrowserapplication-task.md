---
title: UpdateManifestForBrowserApplication タスク | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740216"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> タスクは、[!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] プロジェクトのビルド時に **\<hostInBrowser />** 要素をアプリケーション マニフェスト (*プロジェクト名*.exe.manifest) に追加するために実行されます。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`ApplicationManifest`|必須の **ITaskItem[]** 型のパラメーターです。<br /><br /> `<hostInBrowser />` 要素を追加するアプリケーション マニフェスト ファイルのパスと名前を指定します。|  
|`HostInBrowser`|必須の **Boolean** 型のパラメーターです。<br /><br /> **\<hostInBrowser />** 要素を含めるようにアプリケーション マニフェストを変更するかどうかを指定します。 **true** の場合、新しい `<`**hostInBrowser />** 要素が **\<entryPoint />** 要素に含められます。 要素の挿入は累積的に行われることに注意してください。 **\<hostInBrowser />** 要素が既に存在していても、それが削除または上書きされることはありません。 代わりに、追加の **\<hostInBrowser />** 要素が作成されます。 **false** の場合、アプリケーション マニフェストは変更されません。|  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] は、[!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] 配置を使用して実行されるため、サポート用の配置マニフェストおよびアプリケーション マニフェストと一緒に発行する必要があります。 [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] では [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) タスクを使用して、アプリケーション マニフェストを生成します。  
  
 ブラウザーからホストされるようにアプリケーションを構成する場合は、 **\<hostInBrowser />** 要素をアプリケーション マニフェストに追加する必要があります。次に例を示します。  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 `<hostInBrowser />` 要素を追加するために、[!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] プロジェクトのビルド時に <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> タスクが実行されます。  
  
## <a name="example"></a>例  
 次の例は、アプリケーション マニフェスト ファイルに `<hostInBrowser />` 要素が含まれていることを確認する方法を示しています。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション (WPF) のビルド](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML ブラウザー アプリケーションの概要](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
