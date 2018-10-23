---
title: '方法: ページまたはメモリ内で下 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f49664edc622c9944015c4cea9814a7deb2cfe7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292683"
---
# <a name="how-to-page-up-or-down-in-memory"></a>方法 : [メモリ] ウィンドウの上下スクロール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メモリの内容を表示すると、**メモリ**ウィンドウまたは**逆アセンブル**ウィンドウで、メモリ領域内を上下に移動する、垂直スクロール バーを使用することができます。  
  
### <a name="to-page-up-or-down-in-memory"></a>メモリ内で 1 ページずつ上下に移動するには  
  
1.  1 ページ下に (上位メモリ アドレスに) 移動するには、垂直スクロール バーのスクロール ボックスの下の部分をクリックします。  
  
2.  1 ページ上に (下位メモリ アドレスに) 移動するには、垂直スクロール バーのつまみの上の部分をクリックします。  
  
 垂直スクロール バーの動作が、通常とは異なることもわかります。 最近のコンピューターのアドレス空間はきわめて大きくなっており、スクロール バーのつまみをクリックして任意の位置にドラッグすると、簡単に表示範囲から外れてしまいます。 このため、つまみは "スプリング" のようになっており、ドラッグしても常にスクロール バーの中央に戻ります。 ネイティブ コード アプリケーションの場合、1 ページ単位の上下移動はできますが、自由にスクロールすることはできません。  
  
 マネージド アプリケーションの場合、逆アセンブルは単一関数に限定されており、通常どおりスクロールできます。  
  
 ウィンドウの下部に近づくほど、上位アドレスが表示されることがわかります。 上位アドレスを表示するには、上ではなく下に移動する必要があります。  
  
#### <a name="to-move-up-or-down-one-instruction"></a>1 つ上または 1 つ下の命令に移動するには  
  
-   垂直スクロール バーの上端または下端にある矢印をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [Windows のメモリ](../debugger/memory-windows.md)   
 [方法: [逆アセンブル] ウィンドウの使用](../debugger/how-to-use-the-disassembly-window.md)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)




