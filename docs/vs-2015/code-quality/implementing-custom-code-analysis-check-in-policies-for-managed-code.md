---
title: マネージ コードをカスタム コード分析チェックイン ポリシーの実装 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f0fe69b8afd4a33a783126b6006cbbb5545ba3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548351"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>マネージド コード用のカスタム コード分析チェックイン ポリシーの実装
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[マネージ コードのチェックイン ポリシーを実装するカスタム コード分析](https://docs.microsoft.com/visualstudio/code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code)します。  
  
コード分析チェックイン ポリシーを一連のルールをバージョン管理にチェックインする前に、チーム プロジェクトのメンバーがソース コードに対して実行する必要がありますを指定します。 標準のセットを提供する Microsoft*ルール セット*そのグループのコード分析ルール機能領域に挿入します。 *カスタム チェックイン ポリシーの規則セット*チーム プロジェクトに固有のコード分析規則のセットを指定します。 規則セットは、.ruleset ファイルに格納されます。  
  
 チェックイン ポリシーは、チーム プロジェクト レベルで設定し、バージョン コントロール ツリーの .ruleset ファイルの場所で指定されました。 チームのポリシーのカスタム規則セットのバージョン管理の場所に制限はありません。  
  
 コード分析は、各プロジェクトのプロパティ ウィンドウで各コード プロジェクトに対して構成されます。 コード プロジェクトの設定、カスタム ルールは、ローカル コンピューター上の .ruleset ファイルの物理的な場所によって指定されます。 コード プロジェクトと同じドライブ上にある .ruleset ファイルを指定すると、Visual Studio はプロジェクトの構成ファイルに相対パスを使用します。  
  
 チーム プロジェクトのカスタム規則セットを作成するための推奨される方法では、任意のコード プロジェクトの一部ではない特殊なフォルダーでチェックイン ポリシーの .ruleset ファイルを格納します。 専用のフォルダーにファイルを保存する場合は、ルール ファイルを編集できるユーザーを制限する権限を適用できるディレクトリ構造を簡単に移動することができますを別のディレクトリまたはコンピューターにプロジェクトが含まれます。  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>チーム プロジェクトのカスタム チェックの規則セットを作成します。  
 チーム プロジェクトの設定、カスタム ルールを作成する最初にフォルダーを作成する特殊なチェックイン ポリシーの規則セットの**ソース管理エクスプ ローラー**します。 規則セット ファイルを作成し、バージョン管理にファイルを追加します。 最後に、コード分析チェックイン ポリシー、チーム プロジェクトとして設定するルールを指定します。  
  
> [!NOTE]
>  チーム プロジェクトのフォルダーを作成、最初にマップする必要、チーム プロジェクトのルート、ローカル コンピューター上の場所。 詳細については、次を参照してください。 [(古い) のワークスペースの作成と操作](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2)します。  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>チェックイン ポリシーのルール セットのバージョン管理フォルダーを作成するには  
  
1.  [!INCLUDE[esprtfc](../includes/esprtfc-md.md)]、チーム プロジェクト ノードを展開し、クリックして**ソース管理**します。  
  
2.  **フォルダー**ウィンドウで、チーム プロジェクトを右クリックし、順にクリックします**新しいフォルダー**します。  
  
3.  メインのソース管理 ウィンドウで右クリック**新しいフォルダー**、 をクリックして**の名前を変更**、ルール セットのフォルダーの名前を入力します。  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>チェックイン ポリシーの規則セットを作成するには  
  
1.  **ファイル**メニューで、**新規**、 をクリックし、**ファイル**します。  
  
2.  **カテゴリ**一覧で、**全般**します。  
  
3.  **テンプレート**リストで、ダブルクリック**コード分析規則セット**します。  
  
4.  規則セットに含める規則を指定し、規則セット ファイルを作成したルール セットのフォルダーに保存します。  
  
     詳細については、次を参照してください[カスタム規則セットの作成。](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>規則を追加するには、バージョン管理にファイルを設定します。  
  
1.  **ソース管理エクスプ ローラー**、新しいフォルダーを右クリックし、クリックして**フォルダーに項目の追加**します。  
  
     詳細については、次を参照してください。[バージョン管理を使用して、](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)します。  
  
2.  規則セットを作成したファイルをクリックおよびクリック**完了**します。  
  
     ファイルがソース管理に追加し、チェック アウトしています。  
  
3.  **ソース管理エクスプ ローラー**詳細 ウィンドウ、ファイル名を右クリックし、順にクリックします**保留中の変更をチェックイン**します。  
  
4.  **チェックイン**ダイアログ ボックスで、クリックしてコメントを追加するオプションがある**チェックイン**します。  
  
    > [!NOTE]
    >  チーム プロジェクトのコード分析チェックイン ポリシーを既に構成して、選択した場合、**のみ現在のソリューションの一部であるファイルを含むチェックインを強制**、ポリシー エラーに関する警告がトリガーされます。 ポリシーのエラー] ダイアログ ボックスで、[**ポリシー エラーをオーバーライドし、チェックインを続行**します。 必要なコメントを追加し、クリックして**OK**します。  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>ルールを指定するには、チェックイン ポリシーとしてファイルを設定します。  
  
1.  **チーム**メニューで、**チーム プロジェクトの設定**、 をクリックし、**ソース管理**します。  
  
2.  をクリックして**チェックイン ポリシー**、 をクリックし、**追加**します。  
  
3.  **チェックイン ポリシー**リストで、ダブルクリック**コード分析**、ことを確認し、**マネージ コードに対するコード分析を強制** チェック ボックスをオンします。  
  
4.  **この規則セットを実行**一覧で、 **\<ソース管理からのルール セットの選択 >** します。  
  
5.  バージョン管理でチェックイン ポリシーの規則セット ファイルのパスを入力します。  
  
     パスは、次の構文に従う必要があります。  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  次の手順のいずれかを使用してパスをコピーする**ソース管理エクスプ ローラー**:  
  
    -   **フォルダー**ウィンドウで、規則セット ファイルを含むフォルダーをクリックします。 表示されるフォルダーのバージョン コントロール パスのコピー、**ソース**ボックス、および規則セット ファイルの名前を手動で入力します。  
  
    -   詳細ウィンドウで、規則セット ファイルを右クリックし、**プロパティ**します。 **全般** タブで、値をコピーします**サーバー名**します。  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>コード プロジェクトのチェックイン ポリシーの規則セットへの同期  
 チーム プロジェクト チェックイン ポリシーの規則は、コード プロジェクトのプロパティ ダイアログ ボックスで、コード プロジェクト構成のコード分析規則セットとして設定を指定します。 規則セットは、コード プロジェクトと同じドライブに存在する場合は、相対パスがファイル ダイアログ ボックスからのパスを選択すると、ルール セットを指定する使用されます。 相対パスにより、プロジェクトのプロパティ設定のようなローカル バージョンを使用するその他のコンピューターに移植する制御構造体。  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>チーム プロジェクトの規則を指定するのには、コード プロジェクトの規則のセットとして設定します。  
  
1.  必要に応じて、チェックイン ポリシーの規則セットのフォルダーとファイルをバージョン コントロールから取得します。  
  
     この手順を実行することができます**ソース管理エクスプ ローラー**フォルダーおよび をクリックしを右クリックし、ルールの設定**最新バージョンの取得**します。  
  
2.  **ソリューション エクスプ ローラー**コード プロジェクトを右クリックし、クリックして**プロパティ**します。  
  
3.  **コード分析 をクリック**します。  
  
4.  必要に応じて、適切なオプションをクリックします。、**構成**と**プラットフォーム**を一覧表示します。  
  
5.  指定した構成を使用してコード プロジェクトをビルドするたびにコード分析を実行するには、選択、**を有効にするビルドに対するコード分析 (CODE_ANALYSIS 定数を定義します)** チェック ボックスをオンします。  
  
6.  他の企業からのコンポーネントのコードを無視する選択、**結果生成されたコードを表示しない**チェック ボックスをオンします。  
  
7.  **この規則セットを実行**一覧で、  **\<参照... >** します。  
  
8.  チェックイン ポリシーの規則セット ファイルのローカル バージョンを指定します。


