---
title: IEnumCodePaths2::GetCount |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumCodePaths2::GetCount
helpviewer_keywords:
- IEnumCodePaths2::GetCount
ms.assetid: 988c5092-fcc5-43a1-a94c-c261edd56ebf
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce9d2e183becd0a52cb24c4a62d4eca48616c2e9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281299"
---
# <a name="ienumcodepaths2getcount"></a>IEnumCodePaths2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

列挙体の要素の数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcelt`  
 [out]列挙体の要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドだけを指定する、よく使用される列挙型の COM インターフェイスの一部でない、 `Next`、 `Clone`、 `Skip`、および`Reset`メソッドを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
