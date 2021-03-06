---
title: ResolveNativeReference タスク | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f18549fece2db8a4a758dee17f6b4b1283d97e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996617"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference タスク
ネイティブ参照を解決します。 <xref:Microsoft.Build.Tasks.ResolveNativeReference> クラスを実行します。 このクラスは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。

## <a name="task-parameters"></a>タスク パラメーター
 `ResolveNativeReference` タスクのパラメーターの説明を次の表に示します。

|パラメーター|説明|
|---------------|-----------------|
|`AdditionalSearchPaths`|必須の <xref:System.String?displayProperty=fullName>`[]` 型のパラメーターです。<br /><br /> ネイティブ参照のアセンブリ ID を解決するための検索パスを取得または設定します。|
|`ContainedComComponents`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリの COM コンポーネントを取得または設定します。|
|`ContainedLooseEtcFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ マニフェストに示されているルース *Etc* ファイルを取得または設定します。|
|`ContainedLooseTlbFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリのルース *.tlb* ファイルを取得または設定します。|
|`ContainedPrerequisiteAssemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> マニフェストを使用する前に存在する必要があるアセンブリを取得または設定します。|
|`ContainedTypeLibraries`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリのタイプ ライブラリを取得または設定します。|
|`ContainingReferenceFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 参照ファイルを取得または設定します。|
|`NativeReferences`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> Win32 ネイティブ アセンブリ参照を取得または設定します。|

## <a name="remarks"></a>解説
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。

## <a name="see-also"></a>関連項目
- [タスク](../msbuild/msbuild-tasks.md)
- [タスク リファレンス](../msbuild/msbuild-task-reference.md)