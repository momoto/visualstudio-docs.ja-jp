---
title: メッセージ マーカー | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b668f0331345e6a1022ef79105614f4a22e91d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830079"
---
# <a name="message-markers"></a>メッセージ マーカー
メッセージ マーカーは、ログ出力を表します。 メッセージは、特定のスレッドによって特定の時間に発行される文字列です。 メッセージは、その他のツールで使用するためにテキスト ファイルにエクスポートできます。 メッセージ文字列を確認するには、コンカレンシー ビジュアライザーで、メッセージにポインターを置くことができます。 そして、[マーカー レポート](../profiling/markers-report.md)で、すべてのメッセージ マーカーを確認できます。  次の図は、メッセージ マーカーを示しています。

## <a name="message-aggregation-markers"></a>メッセージの集約マーカー
 コンカレンシー ビジュアライザーで、複数のメッセージが相互に近接しすぎて、個別に描画できないことがあります。 そのような場合には、基になるメッセージを表す*メッセージ集約マーカー*が表示されます。 それらのアイコンのいずれかにポインターを置くと、表現されている、基になるメッセージの数がツールヒントに表示されます。 メッセージを表示するには、ズームインします。  限界までズームインしてもなお集約マーカーが表示される場合には、基になるメッセージを[マーカー レポート](../profiling/markers-report.md)で確認できます。

## <a name="see-also"></a>関連項目
- [コンカレンシー ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)
- [コンカレンシー ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)