---
title: IDebugDocumentText2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43716ce3b01464d2937fd75ce90ec5028679ef47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330641"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
このインターフェイスは、テキスト ドキュメントを表します。

## <a name="syntax"></a>構文

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>実装についてのメモ
 デバッグ エンジン (DE) は、指定する必要があるソース コードがテキスト形式の場合、このインターフェイスを実装します。 以降、DE が実装されている場合は、最も一般的なケースで、これは、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスが実装する必要も、`IDebugDocumentText2`インターフェイス。

## <a name="notes-for-callers"></a>呼び出し元のノート
 使用して、`QueryInterface`からこのインターフェイスを取得するメソッド、`IDebugDocument2`インターフェイス。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 メソッドだけでなく、`IDebugDocument2`インターフェイスでは、このインターフェイスは、次のメソッドを実装します。

|メソッド|説明|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|ドキュメントのこの位置でテキストのサイズを取得します。|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|ドキュメント内の指定した位置からテキストを取得します。|

## <a name="remarks"></a>Remarks
 このインターフェイスを実装するオブジェクトを実装する必要がありますも、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを提供する、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>のためのインターフェイス、 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)オブジェクト。

## <a name="requirements"></a>必要条件
 ヘッダー: msdbg.h

 名前空間: Microsoft.VisualStudio.Debugger.Interop

 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)