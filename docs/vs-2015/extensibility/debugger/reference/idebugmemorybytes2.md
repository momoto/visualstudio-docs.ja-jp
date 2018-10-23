---
title: IDebugMemoryBytes2 |Microsoft Docs
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
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80bf7aa4ad16fd2f213f2761779195b36e126b29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180792"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、メモリのバイト数を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、メモリ内のバイトを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)システム メモリへのアクセスを提供するには、このインターフェイスを返します。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)と[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)オブジェクトのバイトへのアクセスを提供するには、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugMemoryBytes2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|指定した位置から始まるバイト シーケンスを読み取ります。|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|書き込みます`dwCount`で始まるバイト`pStartContext`します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|このインターフェイスによって表されるメモリのバイト単位のサイズを取得します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティの場合、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)配列を表すインターフェイスを提供します、`IDebugMemoryBytes2`その配列内の値にアクセスするインターフェイス。  
  
 Visual Studio の**メモリ ビュー**呼び出し[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)を取得する、`IDebugMemoryBytes2`システム メモリにアクセスするためのインターフェイス。 アクセスできるアドレスを取得、メモリのビューに、アドレスとして入力された式を解析し、使用して、解析された式を評価して[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、`IDebugProperty2`インターフェイス。 呼び出し[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)を返します、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)メモリ アドレスを記述します。 このメモリ コンテキストに渡されます[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)と[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
