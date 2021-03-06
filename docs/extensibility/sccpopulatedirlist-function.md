---
title: SccPopulateDirList 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720895"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 関数
この関数は、確認するディレクトリのリストを指定して、ソース管理に格納するディレクトリと (必要に応じて) ファイルを決定します。

## <a name="syntax"></a>構文

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>パラメーター
 pContext

からソース管理プラグインのコンテキストポインター。

 nDirs

から@No__t_0 配列内のディレクトリパスの数。

 lpDirPaths

から確認するディレクトリパスの配列。

 pfnPopulate

から各ディレクトリパスと (必要に応じて) `lpDirPaths` のファイル名に対して呼び出すコールバック関数 (詳細については、「 [Popdirlistfunc](../extensibility/popdirlistfunc.md) 」を参照してください)。

 pvCallerData

から変更せずにコールバック関数に渡される値。

 限ら

からディレクトリの処理方法を制御する値の組み合わせ (有効な値については、[特定のコマンドで使用される Bitflags](../extensibility/bitflags-used-by-specific-commands.md)の "PopulateDirList flags" セクションを参照してください)。

## <a name="return-value"></a>戻り値
 この関数のソース管理プラグインの実装では、次の値のいずれかが返されることが想定されています。

|[値]|説明|
|-----------|-----------------|
|SCC_OK|操作が正常に完了しました。|
|SCC_E_UNKNOWNERROR|エラーが発生しました。|

## <a name="remarks"></a>Remarks
 コールバック関数に渡されるのは、ソース管理リポジトリ内のディレクトリと (必要に応じて) ファイル名だけです。

## <a name="see-also"></a>関連項目
- [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
- [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [エラー コード](../extensibility/error-codes.md)