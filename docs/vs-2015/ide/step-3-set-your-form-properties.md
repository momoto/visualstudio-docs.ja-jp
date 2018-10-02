---
title: '手順 3: フォームのプロパティの設定 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e60d8fd08cbf75c175bc9e4e9920b04707fb01fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534827"
---
# <a name="step-3-set-your-form-properties"></a>手順 3: フォームのプロパティの設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[手順 3: フォームのプロパティの設定](https://docs.microsoft.com/visualstudio/ide/step-3-set-your-form-properties)します。  
  
次に、**[プロパティ]** ウィンドウを使用してフォームの外観を変更します。  
  
 ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")このトピックのビデオ版については、「[チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 - ビデオ 1](http://go.microsoft.com/fwlink/?LinkId=205209)」または「[チュートリアル 1: C# によるピクチャ ビューアーの作成 - ビデオ 1](http://go.microsoft.com/fwlink/?LinkId=205199)」を参照してください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。  
  
### <a name="to-set-your-form-properties"></a>フォームのプロパティを設定するには  
  
1.  Windows フォーム デザイナーが表示されていることを確認します。 Visual Studio 統合開発環境 (IDE) で、**[Form1.cs [デザイン]]** タブ (Visual Basic では **[Form1.vb [デザイン]]** タブ) をクリックします。  
  
2.  **Form1** フォーム内の任意の場所をクリックして選択します。 **[プロパティ]** ウィンドウに、フォームのプロパティが表示されます。 フォームにはさまざまなプロパティがあります。 たとえば、前景色と背景色、フォームの上部に表示されるタイトルのテキスト、フォームのサイズなどのプロパティを設定できます。  
  
    > [!NOTE]
    >  **[プロパティ]** ウィンドウが表示されない場合は、ツール バーの四角形の **[デバッグの停止]** ボタンをクリックしてプログラムを停止するか、または単にウィンドウを閉じます。 プログラムが停止してもメニュー バーに **[プロパティ]** ウィンドウが表示されない場合は、**[ビュー]**、**[プロパティ ウィンドウ]** の順にクリックします。  
  
3.  フォームを選択したら、**[プロパティ]** ウィンドウで **Text** プロパティを探します。 一覧の並べ替え方法によっては、下へのスクロールが必要になる場合があります。 **[Text]** をクリックし、「**Picture Viewer**」と入力して Enter キーを押します。  フォームのタイトル バーに「**Picture Viewer**」というテキストが表示され、**[プロパティ]** ウィンドウが次の図のようになります。  
  
     ![[プロパティ] ウィンドウ](../ide/media/express-edittextproperty.png "Express_EditTextProperty")  
[プロパティ] ウィンドウ  
  
    > [!NOTE]
    >  プロパティは、項目別またはアルファベット順に並べ替えることができます。 これらの 2 つの表示を切り替えるには、**[プロパティ]** ウィンドウのボタンを使用します。 このチュートリアルでは、アルファベット順で表示した方がプロパティを探しやすくなります。  
  
4.  Windows フォーム デザイナーに戻ります。 フォームの右下のドラッグ ハンドル (次の図の右下にある小さな白い四角形) をクリックします。  
  
     ![ドラッグ ハンドル](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag")  
ドラッグ ハンドル  
  
     このハンドルをドラッグしてフォームのサイズを変更します。ここでは、幅を広げ、高さを少し高くします。  
  
5.  **[プロパティ]** ウィンドウで、**Size** プロパティが変更されたことを確認します。 **Size** プロパティは、フォームのサイズを変更するたびに変更されます。 このプロジェクトに適したフォームのサイズは 550、350 (正確である必要はありません) 程度で、それを目安にフォームのハンドルをドラッグしてください。 あるいは、**Size** プロパティに値を直接入力し、Enter キーを押します。  
  
6.  再度プログラムを実行します。 次のメソッドのいずれかを使用して、プログラムを実行できます。  
  
    -   **F5** キーを押します。  
  
    -   メニュー バーで、**[デバッグ]**、**[デバッグ開始]** の順に選択します。  
  
    -   ツール バーで、**[デバッグ開始]** ボタンを選択します (次の図を参照)。  
  
         ![[デバッグ開始] ツール バー ボタン](../ide/media/express-icondebug.png "Express_IconDebug")  
[デバッグの開始] ツール バー ボタン  
  
     前の手順のときと同様に、IDE でプログラムがビルドおよび実行され、ウィンドウが表示されます。  
  
7.  IDE では実行中のプログラムを変更することはできないため、次の手順に進む前にプログラムを停止しておきます。 次のメソッドのいずれかを使用して、プログラムを停止できます。  
  
    -   ツール バーで、**[デバッグの停止]** ボタンを選択します。  
  
    -   メニュー バーで、**[デバッグ]**、**[デバッグの停止]** の順に選択します。  
  
    -   **[Form1]** ウィンドウの上隅にある X ボタンを選択します。  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
-   チュートリアルの次の手順に進むには、「[手順 4: TableLayoutPanel コントロールを使用したフォームのレイアウトの設定](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 2: プログラムの実行](../ide/step-2-run-your-program.md)」を参照してください。


