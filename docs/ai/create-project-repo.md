---
title: リポジトリを複製する
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539659"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio で Python コードのリポジトリを複製する

[Visual Studio Tools for AI をインストール](installation.md)すると、Python コードのリポジトリを簡単に複製し、それからプロジェクトを作成できます。

1. GitHub リポジトリに接続するには、Visual Studio インストーラーを実行し、**[変更]** を選択し、**[個別のコンポーネント]** タブを選択します。下方にスクロールして **[コード ツール]** セクションを表示し、**[Visual Studio 向け GitHub 拡張]** を選択し、**[変更]** を選択します。

    ![Visual Studio インストーラーでの GitHub 拡張機能の選択](media/create-project-repo/installation-github-extension.png)

2. Visual Studio を起動します。

3. **[表示] > [チーム エクスプローラー]** の順に選択して、**[チーム エクスプローラー]** ウィンドウを開きます。ここでは、GitHub または Azure DevOps に接続したり、リポジトリを複製したりすることができます。

    ![Azure DevOps、GitHub、リポジトリの複製を示すチーム エクスプローラー ウィンドウ](media/create-project-repo/team-explorer-devops.png)

4. **[Local Git Repositories]\(ローカル Git リポジトリ\)** の下の [URL] フィールドに、`https://github.com/Microsoft/samples-for-ai` と入力し、複製されたファイル用のフォルダーを入力し、**[複製]** を選択します。

    > [!Tip]
    > チーム エクスプローラーで指定したフォルダーは、複製されたファイルを受け取る特定のフォルダーです。 `git clone` コマンドとは異なり、チーム エクスプローラーで複製を作成しても、リポジトリの名前のサブフォルダーは自動作成されません。

5. 複製が完了したら、チーム エクスプローラーの下のリポジトリ フォルダーをダブルクリックして、リポジトリのダッシュボードに移動します。 **[ソリューション]** の下で **[新規]** を選択します。

    ![[チーム エクスプローラー] ウィンドウ、複製からの新しいプロジェクトの作成](media/create-project-repo/team-explorer-new-project.png)

6. 表示された **[新しいプロジェクト]** ダイアログで、**[既存の Python コードから]** を選択し、プロジェクトの名前を指定して、**[場所]** をリポジトリと同じフォルダーに設定し、**[OK]** を選択します。 表示されたウィザードで、**[完了]** を選択します。

7. メニューから **[表示]、[ソリューション エクスプローラー]** を選択します。

8. ソリューション エクスプローラーで `TensorFlow Examples> MNIST` ノードを展開し、`convolutional.py` を右クリックし、**[スタートアップ ファイルとして設定]** を選択します。 この手順により、プロジェクトの実行時に使用されるファイルが Visual Studio に指示されます。

9. **Ctrl**+**F5** キーを押すか、**[デバッグ]、[デバッグなしで開始]** の順に選択し、プログラムを実行します。 エラーが表示された場合は、前の手順の作業ディレクトリの設定を再確認します。

10. プログラムが正常に実行されると、そのプログラムによってトレーニングとテスト データセットのダウンロードが開始され、モデルのトレーニングが実行され、エラー発生率が表示されるのがわかります。 時間の経過と共にエラー発生率が低下するようにします。

    ![Python MNIST プログラムからの最初の出力](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda を使用しているときに、numpy の欠落に関するエラーが発生した場合は、[Python 環境を Anaconda を使用するように変更する](../python/selecting-a-python-environment-for-a-project.md)必要があります。

11. TensorBoard で進行状況を視覚化することができます。 プロジェクトを右クリックし、**[Run TensorBoard]\(TensorBoard の実行\)** をクリックして、TensorBoard の出力ログのディレクトリを選択します。

   ![tensorboard を実行する](media/create-project-repo/run-tensorboard.png)

12. 時間の経過に伴いエラーが減少していることに注目してください。これは品質が改善していることを意味します。

   ![tensorboard を実行する](media/create-project-repo/tensorboard.png)
