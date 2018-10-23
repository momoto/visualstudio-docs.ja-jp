---
title: Visual Studio の評価ツール |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5a36822bc4e9a30de69fc67d072c8c40a5159d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292137"
---
# <a name="evaluation-tools-for-visual-studio"></a>Visual Studio の評価ツール
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Visual Studio の職人気質のチェックリスト  
 このチェックリストを使用して、ビジュアルと操作の詳細情報のユーザー エクスペリエンスの品質を評価します。  
  
### <a name="overview"></a>概要  
  
-   すべてのコマンドは、そのコマンドが行われていることをユーザーに指示するフィードバックになることを確認します。  
  
-   すべての UI 要素とコントロールをすべてのテーマとハイ コントラスト モードで表示することを確認します。  
  
-   非アクティブとアクティブな選択が常に区別されている標準とハイ コントラスト モードの両方を確認します。  
  
-   フォーカスが常に表示され、明らかなことを確認します。  
  
### <a name="performance"></a>パフォーマンス  
  
-   いくつかの種類「ビジー」インジケーターのかどうか、コマンドが完了する 1 秒以上が表示されることを確認します。  
  
-   コマンドが完了するには、明示的な進行状況バーか、10 秒以上を受け取る場合ことを確認します (推奨)、不確定不確定なまたはが表示されます。  
  
### <a name="ui-text"></a>UI テキスト  
  
-   すべてのラベルが文またはタイトル文字とテキストが小文字まったくないことを確認します。  
  
    ||そうです|正しくないです。|  
    |-|-------------|---------------|  
    |**コマンド テキスト (すべて)**|文のケース:<br /><br /> **ディレクトリ名:**|ディレクトリ名:|  
    |**ボタンのテキスト (クライアント)**|タイトル ケース:<br /><br /> **[既定に設定する]**|SET AS DEFAULT|  
    |**ボタンのテキスト (オンライン)**|文のケース:<br /><br /> **[既定値として設定]**||  
  
-   グループ ヘッダーと、ボタンを除く、すべてのラベルが最後にコロンとが組み合わされるコントロールの前にことを確認します。  
  
-   省略記号ボタン、コマンド、およびユーザー入力をキャプチャする UI を起動するコマンド リンクが終了することを確認 **[...]**.  
  
     次に例を示します。  
  
    -   **[詳細]** ダイアログ ボックス上のボタンをクリックします。  
  
    -   [ツール] メニューのコマンド オプション (**ツール > オプション**) コマンドの目的は、ダイアログ自体を起動するため、省略記号を取得する必要がありますできません。  
  
-   UI に業界標準の条項を除く、省略形が含まれていないことを確認します。 たとえば、HTML も TCP/IP する必要があります簡潔も OOM (メモリ不足) と PII (個人を特定できる情報) にする必要。  
  
### <a name="keyboard-access"></a>キーボード アクセス  
  
-   キーボードを使用して各タスクを実行する方法があることを確認します。 通常、これは、各コントロールのキーボード アクセスによって実現されますが、一部の高度に視覚化の領域の問題を回避するなど、コード ビューに移動が許容されます。  
  
-   論理的な順序 (左から右、上から下) でのコントロール間を移動することができることを確認します。 これは、ほとんどのコントロールのためのベスト プラクティスが、すべてのコントロールにこのアプローチが必要です。 たとえば、1 つのタブ ストップを持つグループ内のコントロールはそのラジオ ボタンを確認します。  
  
-   すべてのコントロールにラベルがあることと、各ラベルにニーモニックを確認します (例外がいくつかのラベルのないコントロール タブで、ラベル付きコントロールに続く可能性がありますが含まれます)。  
  
-   ニーモニックの競合がないことを確認します。  
  
### <a name="fonts"></a>フォント  
  
-   (フェイス、サイズ、色) のすべてのフォントが一貫して使用して、階層の管理を確認します。  
  
-   すべての UI 要素が、環境フォントのサービスを使用することを確認します。 (を参照してください[Visual Studio のフォントと書式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     サービスを使用しているかを確認するには**ツール > オプション > フォントおよび色**します。 設定のドロップダウンで、環境フォントを選択し、(可読性、コミック San など) 様式上の別のフォント フェイスを変更し、12 pt に、サイズを設定します。 [Ok] をクリックします。 IDE を再起動する必要がありますが、ほとんどの UI をすぐに変更されます。 再起動時にもフォントの変更を認識しない領域は、環境フォントを使用していません。  
  
-   フォント (太字や拡大したテキストなど)、サービスの派生物であるが、サイズ、および環境フォントのサイズが変更されたときに、「通常」のテキストに対する書式設定を保持することを確認します。  
  
-   フォント拡大のための領域のバグがないことを確認します。 クリップを取得するフォントとコントロールの高さを固定または固定の高さのコンテナーの結果は可能性があります。  
  
### <a name="dialogs"></a>ダイアログ ボックス  
  
-   ダイアログのタイトルがそれを起動したコマンドと同じであることを確認します。  
  
-   すべての標準コントロールに、オペレーティング システムの整合性があることを確認します。 標準の背景色は、コントロールには特別な再テンプレート化されたスタイルを標準コントロールから別のように見えることはありません。  
  
-   フォーム内の余白は 12 ピクセルで、一貫性のある表示ことを確認します。  
  
-   ダイアログ ボックスが IDE シェルまたはそれらから派生した子ウィンドウ内で中央揃えで表示されることを確認します。  
  
-   ときに便利ですが、ダイアログ ボックスのサイズを変更できる必要があります。 サイズ変更できるダイアログ ボックス、ダイアログ ボックスの他の部分を一定に保つときに、サイズ変更時に適切な制御する必要がありますサイズすることを確認します。  
  
-   サイズ変更可能なダイアログがあらゆるユーザー調整サイズ (サイズ、場所、ダイアログのコントロールの拡張) を保持することを確認します。  
  
-   タイトル バーにアイコンがないことを確認します。  
  
-   タイトル バーに最小化ボタンがないことを確認します。  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>ダイアログの操作ボタン (VS クライアントのみ)  
  
-   ボタンの操作がこの順序であることを確認: **OK**、**キャンセル**、**適用**します。  
  
-   確認します**OK**と**キャンセル**ボタンは標準のサイズ: 75 x 23 ピクセルです。  
  
-   確認します**OK**と**キャンセル**文字列の長さに関係なく同じサイズのボタンは、します。  
  
-   操作ボタンのラベル、ボタンを標準よりも大きくなる場合は、ことを確認します。 対応する**キャンセル**等しいサイズのボタンは、します。  
  
-   ボタンと関連付けられているコントロール間の 6 ピクセルの余白があることを確認します。  
  
-   いることを確認、 **OK**と**キャンセル**ボタンのニーモニック (アクセス キーに下線付きの文字で定義されている) はありません。  
  
-   その 1 つのボタンを確認します (通常**OK**) 既定でフォーカスがあります。  
  
-   いることを確認**Esc**ダイアログをキャンセル  
  
-   いることを確認**Enter** 」と入力を処理するコントロールにフォーカスがない場合は、既定のボタンを実行します。  
  
-   いることを確認、 **[ok]** と**キャンセル**ボタンがダイアログ ボックスの右下に配置されます。 まれなケースを除き、右上にある垂直方向に積み重ねに許容されるは。  
  
-   他のボタンがダイアログ内で水平方向の配置にある場合にのみ、垂直方向の構成が使用されることを確認します。  
  
### <a name="control-standards"></a>制御標準  
  
#### <a name="general"></a>全般  
  
-   可能であれば、適切な既定値はユーザーの操作と直接ユーザー セーフや一般的な結果に高速化することを確認します。  
  
-   ユーザーは、以前の経験に基づくどうなるかを認識できるようにには標準のコントロールが同じように動作することを確認します。  
  
#### <a name="label-controls"></a>ラベル コントロール  
  
-   各コントロールにラベルがあることと、各ラベルは視覚的に (通常 4 ~ 6 ピクセルの範囲) 内のコントロールと組み合わせて使用とは、他のコントロールの対応するコントロールに近いことを確認します。  
  
-   ラベルがフラッシュに配置されていることを確認します。 コントロールの左上に配置する場合は、左端と左に配置されている場合、ラベルの基準は、入力テキストのベースラインに揃えて配置できるように、水平方向に中央に配置します。  
  
-   いくつかの積み上げラベルと入力コントロールがコントロールの左側に配置されている場合、ラベルが左揃え、ダイアログ ボックスの端から等しい距離、フラッシュしない右とコントロールから等しい距離を確認します。 ペアは、追加の間隔をグループ化を示すために必要な場合を除き、均等に分散する必要があります。  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>入力コントロール (テキスト ボックス、コンボ ボックス)  
  
-   環境の既定のフォントを使用する場合は、テキスト ボックス、コンボ ボックスとボタンの表示の高さ 23 のすべてのピクセルとはことを確認します。  
  
-   ヒント テキストを使用する場合は、色に設定されていることを確認`Environment.ControlEditHintText`色サービスを使用します。  
  
-   フィールドが必須のフィールドとして識別する必要がありますの場合は、次のコマンドを確認します。  
  
    -   バック グラウンドに設定されている`Environment.ControlEditRequiredBackground`に設定されているフォア グラウンドと `Environment.ControlEditRequiredHintText`  
  
    -   内でのコントロールとして表示されるヒント テキストが **"\<必要 >"**  
  
#### <a name="button-controls"></a>ボタン コントロール  
  
-   長いテキストに対応しない限り、ボタンの 75 x 23 (ピクセル単位) の最小サイズを確認します。  
  
-   ボタンが残っているし、右余白を 3 ~ 5 (ピクセル単位) と同様のコンテンツの余白を確認します。  
  
-   省略記号のみを含む小さな正方形のボタンを使用することができます **[...]** の代わりに、 **[参照...]** ボタン (または同様の機能)。 使用する場合は、ボタンが 23 x 23 のサイズを確認します。  
  
-   1 つ以上を使用する必要がある場合 **[参照...]** 、ダイアログにボタンをクリックし、いることを確認短縮バージョン (省略記号のみ **[...]**) すべてに使用されます。  
  
-   その省略記号を確認します **[...]。** ボタンのニーモニックはありません。 横にある入力コントロールにフォーカスがある場合、1 つのタブは、省略記号ボタンにフォーカスを移動する必要があります。  
  
-   確認ボタン、コマンド、および複数のユーザー入力をキャプチャするセカンダリ UI を起動するコマンド リンクは、省略記号で終了する必要があります **[...]**.  
  
#### <a name="hyperlinks"></a>ハイパーリンク  
  
-   ハイパーリンク コントロールにアクティブな際の赤が点滅しないことを確認します。 これは、色のサービスが使用されているいないこと、インジケーター  
  
-   VS の色が使用されるを確認します。  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   ハイパーリンクが段落に埋め込まれている場合を除き、下線なしで青に表示されることを確認します。  
  
#### <a name="check-boxes"></a>チェック ボックス  
  
-   チェック ボックスに複数行のテキストがある場合は、ボックスが連携しないすべての行の間で垂直方向に中央揃えのテキストの最初の行を確認します。  
  
-   確認チェック ボックスを常にバイナリの選択肢を示すとはしないユーザーを移動しますまたは新しいウィンドウまたはページを開きます。  
  
-   チェック ボックスは、入力コントロールに関連するオプションを提示する場合は、ポインタ フラッシュ左と非常に近いの関係を示すには、その管理下にあることを確認します。  
  
-   チェック ボックスが**決して**ダイアログまたはページの内容全体を有効にするための手段として使用します。  
  
#### <a name="group-boxes"></a>グループ ボックス  
  
-   ダイアログ ボックスが、ダイアログ ボックスの内容全体を含む 1 つのグループ ボックス内に含まれていないことを確認します。  
  
-   各グループ ボックス内の少なくとも 2 つのコントロールがあることを確認します。  
  
-   2 つ以上のグループ ボックス、ダイアログ ボックスであることはほとんどありませんはずです。  
  
-   入れ子になったグループ ボックスがないことを確認します。  
  
### <a name="icons"></a>アイコン  
  
-   ダーク テーマで、アイコン正しく反転表示にされることを確認します。  
  
-   すべてのアイコンが主要な概念に基づいていることを確認します。  
  
-   各アイコンは個別のわかりやすい、(なし状態修飾子/言語) の 3 つ以上の概念が含まれていないことを確認します。  
  
-   基本のアイコンが表示されること、領域内で中央揃えを確認します。  
  
-   すべてのアイコンが読みハイ コントラスト モードで表示されることを確認します。  
  
-   使用する色が使用状況の標準の色に揃えて配置することを確認します。  
  
-   アイコンの周囲には、ハロー (境界線) がないことを確認します。 (存在する場合は、ハローは隣接する UI の背景色一致する必要があります。)  
  
### <a name="touch-enabled-ui"></a>タッチ対応の UI  
  
-   対話型コントロールが簡単に押せる – 最小にするのに十分な大きさであることを確認**23 x 23 ピクセル**サイズ  
  
-   最もよく使用されるコントロールが以上であることを確認**40 x 40 ピクセル**サイズ。  
  
-   対話型コントロールが以上であることを確認**の間隔が 5 ピクセル**それらの間
