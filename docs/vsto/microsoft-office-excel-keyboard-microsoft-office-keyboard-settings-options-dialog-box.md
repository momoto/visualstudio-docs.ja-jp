---
title: Office Excel キーボード、キーボードの設定オプション ダイアログ ボックス
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836037"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定、オプション ダイアログ ボックス
  Microsoft Office Excel および Visual Studio 両方のショートカット キーを処理します。 同じショートカット キーの組み合わせは、Excel と Visual Studio でのさまざまなコマンドのスタンバイことができます。 Excel のドキュメント レベルのプロジェクトで Visual Studio で開くとき、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受け取ります。 既定では、Visual Studio がショートカット キー、すべてのコマンドを受け取りますが、Excel のドキュメントにフォーカスがある場合は、選択して、受信を行うことができます**ダイナミック キーボード スキーム**します。

 ショートカット キーを現在処理しているアプリケーションでのコマンドに割り当てられていないショートカット キーを使用する場合は、他のアプリケーションへショートカット キーが渡されます。

 選択したオプションは、変更するまで Excel プロジェクトを有効になります。 選択範囲では Microsoft Office Word のプロジェクトには影響しませんMicrosoft Office Word キーボード オプションを使用して Word の変更を行う必要があります。

## <a name="uielement-list"></a>UIElement の一覧
 **Visual Studio のキーボード スキーム**Excel にフォーカスがある場合でも、Visual Studio がショートカット キー、すべてのコマンドを受信します。 たとえば、ファンクション キーを押して**F5** Excel にフォーカスがある Visual Studio は、ソリューションのデバッグを開始します。

 **ダイナミック キーボード スキーム**フォーカスがある場合にのみ、Visual Studio がショートカット キーのコマンドを受信します。 Excel にフォーカスがある場合は、Excel は、すべてのショートカット キーのコマンドを受信します。 たとえば、次の関数キーを押す**f5 キーを押して**Excel にフォーカスがある、Excel が表示されます、**ジャンプ** ダイアログ ボックス。 キーを押す場合**F5** Visual Studio にフォーカスがある Visual Studio は、ソリューションのデバッグを開始します。

## <a name="see-also"></a>関連項目
- [Microsoft Office Word キーボード、Microsoft Office Keyboard 設定、オプション ダイアログ ボックス](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
