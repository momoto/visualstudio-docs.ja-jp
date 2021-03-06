---
title: Date オブジェクトが必要です。 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572902"
---
# <a name="date-object-expected"></a>データ オブジェクトが必要です。
`Date`以外の型のオブジェクトに対して、**日付のプロトタイプ**または**日付のプロトタイプ**メソッドを呼び出そうとしました。 この種類の呼び出しのオブジェクトは `Date`型である必要があります。 例 :  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `Date`型のオブジェクトに対して**のみ、メソッドを呼び**出すことができ**ます。**  
  
## <a name="see-also"></a>参照  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [GetDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [組み込みオブジェクト](../../javascript/intrinsic-objects-javascript.md)