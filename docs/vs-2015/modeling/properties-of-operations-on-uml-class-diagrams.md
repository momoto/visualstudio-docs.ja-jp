---
title: クラス ダイアグラムの UML での操作のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e977ede02f355724f1a93f82f1c688de27e36fa6
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592718"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML クラス ダイアグラムの操作のプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML での操作のプロパティにクラス ダイアグラム](https://docs.microsoft.com/visualstudio/modeling/properties-of-operations-on-uml-class-diagrams)します。  
  
UML クラス図で追加できます*操作*クラスとインターフェイスにします。 操作とは、クラスまたはインターフェイスのインスタンスが実行できるメソッドまたは関数です。  
  
 操作を追加するには、クラスまたはインターフェイスを右クリックして**追加**、 をクリックし、**操作**します。  
  
 図のクラスの操作が表示されない場合は、クラスまたはインターフェイスの上部にある展開用シェブロンをクリックします。 表示できる場合、**操作**ヘッダー、 をクリックして **[+]** 操作セクションを展開します。  
  
## <a name="signature-of-an-operation"></a>操作の署名  
 操作のシグネチャは、UML クラス図のクラスまたはインターフェイスで操作を表すテキスト行です。 次の書式を使用します。  
  
 \+ OperationName (parameter1: Type1 [*]、...): ReturnType [\*]  
  
 \+ パブリックな可視性を表します。 これ以外に指定できる値は、- (プライベート)、# (保護)、~ (パッケージ) です。  
  
 `OperationName` 場合に下線を引く、 **Is Static**プロパティが true の場合が斜体場合、 **Is Abstract**プロパティは true。  
  
 戻り値の型が定義されていない場合、`: ReturnType` は省略されます。  
  
 `[*]` は、パラメーターまたは戻り値の型の多重度を表します。 多重度が 1 の場合は省略されます。  
  
 これらのプロパティの詳細については、次のセクションを参照してください。  
  
## <a name="properties"></a>プロパティ  
 これらは、UML クラス図のクラスまたはインターフェイス内の操作のプロパティです。  
  
 操作のプロパティを表示するダイアグラムで、クラスまたはインターフェイスで操作を右クリックし をクリックし、**プロパティ**します。 プロパティが表示されます、**プロパティ**ウィンドウ。  
  
|プロパティ|既定値|説明|  
|--------------|-------------|-----------------|  
|**Name**|(新しい名前)|含んでいる型内で一意である必要があります。|  
|**パラメーター**|(なし)|フォームを含む一覧_名前_**:**_型_**、** _名前_**:** _型_**、.** クリックして **[...]** 一覧を編集します。<br /><br /> 型にはプリミティブ型、または、モデル内で定義されている型があります。 このプロパティに新しい型の名前を入力すると、UML モデル エクスプローラーの **[未指定の型]** セクションに型が 1 つ追加されます。|  
|**戻り値の型**|(なし)|**(なし)**、プリミティブ型、または、モデルで定義されている型。 このプロパティに新しい型の名前を入力すると、UML モデル エクスプローラーの **[未指定の型]** セクションに型が 1 つ追加されます。|  
|**事後条件**|(なし)|操作の実行の前と後におけるシステムの状態間の関係を指定するオプションの条件。|  
|**前提条件**|(なし)|操作の実行の前と後におけるシステムの状態に関する前提条件を指定するオプションの条件。|  
|**ボディの条件**|(なし)|操作によって返される値に関する、オプションの制約。|  
|**可視性**|Public|許可されている値と、署名に表示される文字は、以下のとおりです。<br /><br /> **+ Public** - グローバルに参照できる<br /><br /> **- Private** - 所有元の型の外部では参照できない<br /><br /> **# Protected** - 所有元から派生した型では参照できる<br /><br /> **~ Package** - 同じパッケージ内の他の型で参照できる|  
|**署名**|+*名前*)|この操作の可視性、名前、パラメーター、および戻り値の型を要約します。 図で署名を編集するか、個々 のプロパティを編集することで、これらのプロパティを変更できます。|  
|**作業項目**|関連付けなし|関連付けられている作業項目の数。 読み取り専用。<br /><br /> 詳細については、次を参照してください。[モデル要素をリンクし、作業項目](../modeling/link-model-elements-and-work-items.md)します。|  
|**コンカレンシー**|Sequential|**シーケンシャル**-操作がまたは同時実行制御なしで設計されます。 この操作を同時に呼び出すと、エラーが発生する可能性があります。<br /><br /> **保護された**-他のインスタンスが完了するまで、操作は自動的にブロックします。<br /><br /> **同時実行**-操作は複数の呼び出しが同時に実行できるように設計されています。|  
|**静的します。**|False|True の場合、この操作は、この種類のすべてのインスタンス間で共有されます。<br /><br /> True の場合、図では下線が付けられた状態で操作名が表示されます。|  
|**抽象型**|False|True の場合、この操作にはコードが関連付けられていません。 そのため、所有元のクラスは抽象になります。|  
|**リーフには**|False|設計者は、この操作は、派生クラスでオーバーライドできないと想定しています。|  
|**クエリは、します。**|False|True の場合、この操作によって、システムの状態に対して有意な変更は行われません。 そのため、システムの状態を確認するテストなどで使用できます。|  
|**多重度**|1|**1** -指定した型の 1 つの値。<br /><br /> **0..1** -できる`null`します。<br /><br /> \* -指定した型の値のコレクション。<br /><br /> **1..\***  - 少なくとも 1 つの値を含むコレクション。<br /><br /> *n* `..` *m* -間を含むコレクション`n`と`m`値。|  
|**順序付け**|False|true の場合、コレクションは順序付きリストの形式です **多重度**1 つ以上の。|  
|**一意では**|False|true の場合、コレクション内に重複値は存在しません。 **多重度**1 つ以上の。|  
  
## <a name="see-also"></a>関連項目  
 [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)   
 [UML クラス ダイアグラムで型のプロパティ](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML クラス図の属性のプロパティ](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML クラス図の関連付けのプロパティ](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)


