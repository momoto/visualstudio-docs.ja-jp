---
title: Visual Basic でサポートされていない編集エディット コンティニュ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44dea7dd67653a5dbde95f10a331932a9c8c14c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534525"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Visual Basic エディット コンティニュでサポートされていない編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Basic エディット コンティニュでサポートされていない編集](https://docs.microsoft.com/visualstudio/debugger/unsupported-edits-in-visual-basic-edit-and-continue)します。  
  
エディット コンティニュでは、プログラムの実行を中断モードで停止し、実行中のコードに変更を加え、変更結果を反映してプログラムを再開できます。 通常、クラスのパブリック構造体に影響を及ぼす宣言コードの編集は禁止されています。ただし、クラス内のメソッド、プロパティ本体、またはプライベート宣言に対しては、多くの編集を行うことができます。  
  
 サポートされていない変更を行う必要がある場合は、デバッグを停止し、変更を加えた後で新しいデバッグ セッションを開始します。  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> メソッドおよびプロパティ本体の編集  
 **静的ローカル変数への変更がサポートされていない**: 追加や、ローカル変数を更新して、コンパイル エラーが発生する場合は、静的ローカル変数を削除します。  
  
 **サポートされていないジェネリック変更**: ジェネリック メソッド自体またはジェネリック メソッドの本体の変更はサポートされていません。 ただし、ジェネリック型のインスタンス化や既存のジェネリック メソッドへの呼び出しは追加、削除、または変更できます。  
  
 **サポートされていないその他の変更**  
  
-   呼び出し履歴に存在するメソッドの呼び出しステートメントの変更  
  
-   `Try...Catch` ブロックの追加 (命令ポインターが最終的に `Catch` ブロックまたは `Finally` ブロックに存在する場合)  
  
-   削除、`Try...Catch`が命令ポインターの場合は、ブロック、`Catch`ブロックまたは`Finally`ブロックします。  
  
-   現在の命令ポインターの周囲への `Using` ブロックの追加  
  
-   現在の命令ポインターの周囲への `SynchLock` ブロックの追加  
  
###  <a name="BKMK_AttributeEdits"></a> 属性の編集  
 エディット コンティニュでは、属性の変更はサポートされません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   属性クラスの定義、編集、または削除。  
  
-   属性の追加。  
  
-   既存の属性の編集または削除。  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> クラス宣言の編集  
 中断モードでは、エディット コンティニュはクラス宣言に対するほとんどの変更を許可しません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   既存のクラスの継承の名前変更、削除、または変更  
  
-   新しいインターフェイスの実装、または既存のインターフェイスの実装の削除  
  
-   クラスの修飾子の変更  
  
-   `ComClass` ステータスの追加、変更、または削除  
  
-   ジェネリック クラス宣言の編集  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> クラス メンバー宣言の編集  
 エディット コンティニュではほとんどの場合、メンバー宣言に対する変更は禁止されています。 たとえば、メンバーの署名またはアクセス レベルを変更することはできません。またコンパイル エラーが発生する場合は、メンバーを完全に削除できません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   既存メンバー変数を含むブロック内で同名のグローバル変数またはメンバー変数を宣言することによる既存メンバー変数のシャドウ  
  
-   ブロック内で新しいインスタンスを宣言することによる静的ローカル変数のシャドウ  
  
-   イベント ハンドラーの削除  (イベント ハンドラーの追加は可能)  
  
-   新しいオーバーロード プロパティまたはメソッドの追加 (ただし、そのプロパティまたはメソッドが `Private` であり、どのアクティブ ステートメントにもその名前がない場合を除く)  
  
-   メンバー変数に対する `WithEvents` 句の追加と削除  
  
-   メンバーの削除  
  
-   インターフェイスの実装を停止する、プロパティ宣言またはメソッド宣言の変更  
  
-   ジェネリックを使用するメソッドの編集  
  
-   非プライベート プロパティまたはメソッドのシグネチャまたは戻り値の型の変更  
  
-   基底クラスのメンバーのオーバーライドとシャドウ  
  
-   `SequentialLayout` または `ExplicitLayout` とマークされている任意のクラスでの新しいフィールドの追加  
  
-   メソッドの `MustInherit` ステータスまたは `NotOverridable` ステータスの変更  
  
-   プロパティまたはメソッドのアクセス修飾子の変更  
  
-   フィールドの型または読み取り専用ステータスの変更  
  
-   パブリック フィールドの変更  
  
###  <a name="BKMK_CompilerOptionEdits"></a> コンパイラ オプションの編集  
 エディット コンティニュを中断モードで使用している間は、次のコンパイラ オプションを変更、追加、または削除できません。  
  
-   **Option Strict**  
  
-   **Option Explicit**  
  
-   **Option Compare**  
  
###  <a name="BKMK_ConstantsEdits"></a> 定数の編集  
 エディット コンティニュ モード中の定数への変更は、厳しく制限されています。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   定数変数の追加または更新。  
  
-   定数の型または値の変更。  
  
-   定数の削除。  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> デリゲートおよびイベント宣言の編集  
 エディット コンティニュでは、中断モードでのデリゲートとイベントへの変更は認められない場合もあります。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   デリゲート定義の変更または削除  
  
-   イベントの削除  
  
###  <a name="BKMK_EnumerationEdits"></a> 列挙型の編集  
 エディット コンティニュでは、中断モード中の列挙型 (`Enums`) の変更は認められていません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   `Enum` の基になる型の変更  
  
-   `Enum` メンバーの追加、変更、または削除  
  
-   `Enum` のアクセス修飾子の変更  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> 外部宣言の編集  
 通常、エディット コンティニュでは外部メソッドの宣言を変更できません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   外部宣言の追加または削除  
  
-   外部宣言のシグネチャまたはマーシャリング属性の変更  
  
###  <a name="BKMK_ImportsEdits"></a> Imports の編集  
 エディット コンティニュでは、中断モードで `Imports` ステートメントを追加、変更、または削除できません。  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> インターフェイス定義の編集  
 一般に、インターフェイスを実装するメンバーに変更を加えることはできますが、インターフェイス定義自体を変更することは、通常はエディット コンティニュによって禁止されています。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   インターフェイス メンバーの追加、変更、削除  
  
-   既存のインターフェイスの削除  
  
-   インターフェイスのアクセス修飾子の変更  
  
-   インターフェイス継承階層の変更  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> モジュール宣言の編集  
 中断モードでは、エディット コンティニュはモジュール宣言に対するほとんどの変更を許可しません。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   新しいモジュールの作成  
  
-   既存のモジュールの名前変更または削除  
  
-   モジュールのアクセス修飾子の変更  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> モジュール メンバー宣言の編集  
 エディット コンティニュを使用すると、中断モード中にプロパティ、メソッド、およびフィールドなどのモジュール メンバーにさまざまな変更を加えることができます。 ただし、変更の内容によってはサポートされない場合があります。 特に、エディット コンティニュは、メンバーの型やシグネチャの追加、削除、および変更をサポートしません。  
  
 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   新しいメンバーの追加。ただし、どのアクティブ ステートメントにもメンバーの名前がない場合を除きます。  
  
-   プロパティまたはメソッドの削除  
  
-   プロパティまたはメソッドのシグネチャの変更  
  
-   フィールドの追加、名前変更、移動、または削除。  
  
-   ジェネリックを使用するメソッドの編集  
  
-   プロパティまたはメソッドのアクセス修飾子の変更 (`Public` から `Private` への変更など)  
  
-   既存のフィールドの型の削除または変更  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> 入れ子にされた型の宣言の編集  
 エディット コンティニュでは、入れ子になった型を別の名前空間または型に移動することはサポートされません。  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> 構造体の宣言の編集  
 エディット コンティニュのでは、構造体の宣言に対するほとんどの変更は許可されていない**中断**モード。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   既存の構造体の名前の変更または削除  
  
-   新しいインターフェイスの実装、または既存のインターフェイスの実装の削除  
  
-   構造体のアクセス修飾子の変更  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> 構造体メンバー宣言の編集  
 エディット コンティニュを使用すると、中断モードで、構造体メンバー (プロパティ、メソッド、およびフィールド) にさまざまな変更を加えることができます。 ただし、構造体メンバーの宣言に影響を及ぼす変更など、サポートされていない変更もあります。 具体的には、エディット コンティニュでは次の変更はサポートされません。  
  
-   プロパティまたはメソッドの削除  
  
-   フィールドの追加または削除  
  
-   プロパティまたはメソッドのシグネチャの変更  
  
-   ジェネリックを使用するメソッドの編集  
  
-   プロパティ宣言とメソッド宣言のどちらがインターフェイスを実装するかの変更  
  
-   プロパティまたはメソッドのアクセス修飾子を変更する (たとえば、変更`Public`に**プライベート**)。  
  
-   フィールドの削除  
  
-   フィールドの種類の変更  
  
## <a name="see-also"></a>関連項目  
 [方法: エディット中断モードで編集を適用して続行](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [エディット コンティニュ (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)


