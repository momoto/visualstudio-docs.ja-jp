---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ab3a9076afc4dab4af2ec4f24dffa60fa65dae2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174890"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

シンボルのグループ内のモジュールに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```csharp  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCount`  
 [in]内のモジュールの数、`ppGuids`配列。  
  
 `ppGuids`  
 [in]モジュールの一意の識別子を含む配列。  
  
 `pADIds`  
 [in]アプリケーション ドメインの識別子です。  
  
 `pCurrentState`  
 [in]シンボルのグループの現在の状態。  
  
 `ppCDModItfs`  
 [out]シンボルのグループ内のモジュールを格納しているオブジェクトを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
