---
title: 'チュートリアル: アウトライン | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df269c3018d850ed2d5ae7435b82eb4f3aee4e1a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320624"
---
# <a name="walkthrough-outlining"></a>チュートリアル: アウトライン
アウトラインの展開または折りたたみをするテキスト領域の種類を定義することでなどの言語ベースの機能を設定します。 言語サービスのコンテキストで領域を定義して独自ファイル名拡張子とコンテンツ タイプを定義し、または領域の定義をその型だけに適用するか、または領域の定義を ("text") などの既存のコンテンツ タイプに適用できます。 このチュートリアルでは、定義のアウトライン領域を表示する方法を示します。

## <a name="prerequisites"></a>必須コンポーネント
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトを作成します。

### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには

1. VSIX プロジェクトを作成する。 ソリューション `OutlineRegionTest`の名前を指定します。

2. エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。

3. 既存のクラス ファイルを削除します。

## <a name="implement-an-outlining-tagger"></a>アウトラインのタガーを実装します。
 アウトライン領域がある種のタグでマークされている (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>)。 このタグは、標準の動作のアウトラインを提供します。 アウトライン表示の領域を展開または折りたたむことができます。 アウトライン表示の領域がプラス記号でマークされている ( **+** ) またはマイナス記号 a が折りたたまれている場合 ( **-** ) が展開されていて、展開された領域が縦線で区分されています。

 次の手順は、角かっこで区切られたすべての領域のアウトライン領域を作成するタガーを定義する方法を示します ( **[** 、 **]** )。

### <a name="to-implement-an-outlining-tagger"></a>アウトラインのタガーを実装するには

1. クラス ファイルを追加し、その名前を `OutliningTagger`にします。

2. 次の名前空間をインポートします。

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. という名前のクラスを作成する`OutliningTagger`、実装すること<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. アウトライン領域としてタグ付けする必要があります行のセットを蓄積して、テキスト バッファーとスナップショットを追跡するためにいくつかのフィールドを追加します。 このコードには、(後で定義) にアウトライン領域を表す領域オブジェクトの一覧が含まれています。

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. バッファーを解析し、イベント ハンドラーを追加、フィールドを初期化するタガー コンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>にまたがるメソッドで、タグをインスタンス化します。 この例では、範囲、<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>メソッドに渡されたは、大文字と小文字が常にする場合がありますいないが、連続します。 このメソッドは、アウトライン領域の新しいタグの範囲をインスタンス化します。

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 宣言を`TagsChanged`イベント ハンドラー。

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 追加、`BufferChanged`に応答するイベント ハンドラー<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>テキスト バッファーを解析することによってイベント。

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. バッファーを解析するメソッドを追加します。 ここに示す例は、例示のみを目的があります。 バッファーは、入れ子になったのアウトライン領域に同期的に解析します。

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 次のヘルパー メソッドは、1 が一番左中かっこのペアになるように、アウトライン レベルを表す整数を取得します。

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 次のヘルパー メソッドは、(この記事の後半で定義される) 領域を SnapshotSpan に変換します。

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 次のコードでは、例示のみを目的です。 行番号とアウトライン領域、および (存在する場合) の親領域への参照の開始のオフセットを含む PartialRegion クラスを定義します。 このコードでは、アウトライン領域を入れ子になったを設定するためにパーサーを使用できます。 リージョンの派生クラスには、アウトライン領域の最後の行番号への参照が含まれています。

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>タガー プロバイダーを実装します。
 タガーのタガー プロバイダーをエクスポートします。 タガー プロバイダーを作成、 `OutliningTagger` 「テキスト」コンテンツの種類、または他の返しますのバッファーの場合、 `OutliningTagger` 1 つは、バッファーが既にある場合。

### <a name="to-implement-a-tagger-provider"></a>タガー プロバイダーを実装するには

1. という名前のクラスを作成する`OutliningTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ContentType と TagType 属性を持つエクスポート。

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 実装、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>メソッドを追加することで、`OutliningTagger`バッファーのプロパティにします。

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト
 このコードをテストするには、OutlineRegionTest ソリューションをビルドし、実験用インスタンスで実行します。

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>ビルドして OutlineRegionTest ソリューションをテストするには

1. ソリューションをビルドします。

2. デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。

3. テキスト ファイルを作成します。 左かっこと右角かっこの両方を含むいくつかのテキストを入力します。

    ```
    [
       Hello
    ]
    ```

4. 両方の角かっこを含むアウトライン領域が必要です。 始めかっこの左側にアウトライン領域を折りたたむにマイナス記号をクリックする必要があります。 ときに領域が折りたたまれている、省略記号 ( *.* ) 折りたたまれた領域とテキストを含むポップアップの左に表示する**ホバー テキスト**省略記号上にポインターを移動するときに表示する必要があります。

## <a name="see-also"></a>関連項目
- [チュートリアル: コンテンツの種類をファイル名拡張子にリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)