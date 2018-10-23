---
title: コマンド ライン パラメーターを使用して、Visual Studio をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 6266626d2eb60b64f1923a0c3f54d39c9b20072a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268607"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>コマンド ライン パラメーターを使用して、Visual Studio をインストールするには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。[コマンド ライン パラメーターを使用して、Visual Studio 2017 をインストールする](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio)します。

コマンド プロンプトから Visual Studio 2015 をインストールする場合は、次のコマンド ライン パラメーター (スイッチとも呼ばれます) を使用することができます。  
  
> [!NOTE]
>  ブートス トラップ ファイルではなく、実際のインストーラーを使用することを確認します。 使用するかどうかを確認、 **`vs_enterprise.exe`** vs_enterprise_ ではなく*GUID*.exe です。 インストーラーをダウンロードする[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)します。  
  
## <a name="list-of-command-line-parameters"></a>コマンド ライン パラメーターの一覧  
 Visual Studio のコマンド ライン パラメーターでは、大文字と小文字は区別されません。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**/?**<br /><br /> **/help**<br /><br /> **/h**|コマンド ライン パラメーターを表示します。|  
|**/AddRemoveFeatures**|インストールされている製品に追加または削除する機能を指定します。|  
|**/AdminFile** *AdminDeployment.xml*|管理用インストールに指定したデータ ファイルを使用して Visual Studio をインストールします。|  
|**/ChainingPackage** *BundleName*|このバンドルをチェーンするバンドルを指定します。 カスタマー エクスペリエンス向上コホートの指定にも使用できます。|  
|**/CreateAdminFile\<ファイル名 >**|/AdminFile と組み合わせて使用できるコントロール ファイルを作成する場所を指定します。|  
|**/CustomInstallPath** *インストール ディレクトリ*|指定したディレクトリに再ターゲット可能パッケージをすべてインストールします。|  
|**/ForceRestart**|インストール後に必ずコンピューターを再起動します。|  
|**完全/**|すべての製品の機能をインストールします。|  
|**/InstallSelectableItems\<項目名 1 > [;\<項目名 2 >]**|インストーラー ウィザードの選択画面でチェックする選択ツリー項目の一覧。|  
|**/l**<br /><br /> **/ログ***ファイル名*|ログ ファイルの場所を指定します。|  
|**/layout** *ディレクトリ*|インストール メディアのファイルを指定したディレクトリにコピーします。|  
|**/NoCacheOnlyMode**|パッケージ キャッシュの事前設定を防ぎます。|  
|**/NoRefresh**|必須の更新バージョンまたは推奨の更新バージョンに関して、この製品の新しいバージョンをチェックしないようにします。|  
|**/norestart**|インストール中またはインストール後に、インストール アプリケーションによりコンピューターが再起動されないようにします。 リターン コードを参照してください、 [Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)を検索するリターン コード。|  
|**/noweb**|インターネットからインストールされないようにします。|  
|**/OverrideFeedUri\<フィード ファイルへのパス >**|ローカルへのパス。ソフトウェア項目を説明する外部フィード。|  
|**/ProductKey**<br /><br /> *ProductKey*|ダッシュと 25 を超える文字を含まないカスタム プロダクト キーを設定します。|  
|**/PromptRestart**|コンピューターを再起動する前にユーザーに確認します。|  
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|インストール アプリケーションのユーザー インターフェイス (UI) を非表示にします。 Visual Studio が既にインストールされている場合に、このパラメーター以外のパラメーターを指定しないと、インストール アプリケーションはメンテナンス モードで実行されます。|  
|**/qb**<br /><br /> **/passive**|進行状況が表示されますが、ユーザーの入力を待ちません。|  
|**/repair**|Visual Studio を修復します。|  
|**/SuppressRefreshPrompt**|インストール ウィザードに更新プログラムの入手可能ダイアログが表示されないようにし、必須の更新バージョンまたは推奨の更新バージョンが存在する場合に、インストール ウィザードで自動的に受け入れられるようにします。|  
|**/u**<br /><br /> **/アンインストールします。**|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]をアンインストールします。|  
|**/Uninstall/Force**<br /><br /> **/u/force**|Visual Studio および他の製品と共有するすべての機能をアンインストールします。 **警告:** このパラメーターを使用する場合、同じコンピューターにインストールされているその他の製品が正しく機能しているを停止する可能性があります。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 管理者ガイド](../install/visual-studio-administrator-guide.md)