---
title: LINQ to SQL クラス間のリレーションシップ (O/R デザイナー)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13443dd25719caad5002b29a33975a0dbc5850f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641898"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>方法: LINQ to SQL クラス間の関連付けを作成する (O/R デザイナー)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] のエンティティ クラス間の関連付けは、データベース内のテーブル間の関連付けに似ています。 **[関連付けエディター]** ダイアログ ボックスを使用することで、エンティティ クラス間の関連付けを作成できます。

**[関連付けエディター]** ダイアログ ボックスを使用して関連付けを作成するときは、親クラスと子クラスを選択する必要があります。 親クラスは、主キーを含むエンティティ クラスであり、子クラスは、外部キーを含むエンティティ クラスです。 たとえば、`Northwind Customers` テーブルと `Orders` テーブルにマップするエンティティクラスを作成した場合、`Customer` クラスは親クラスになり、`Order` クラスは子クラスになります。

> [!NOTE]
> **サーバーエクスプローラー**または**データベースエクスプローラー**から**オブジェクトリレーショナルデザイナー** (**O/R デザイナー**) にテーブルをドラッグすると、データベース内の既存の外部キーリレーションシップに基づいてアソシエーションが自動的に作成されます。

## <a name="association-properties"></a>関連付けのプロパティ
関連付けの作成後、**O/R デザイナー**で関連付けを選択すると、 **[プロパティ]** ウィンドウにいくつかの構成可能なプロパティが表示されます。 (関連付けは関連するクラス間の線です)。次の表は、関連付けのプロパティの説明を示しています。

|property|説明|
|--------------|-----------------|
|**カーディナリティ**|関連付けが 1 対多と 1 対 1 のどちらであるかを制御します。|
|**子プロパティ**|コレクションのプロパティを親に作成するか、子レコードへの参照を関連付けの外部キー側に作成するかを指定します。 たとえば、`Customer` と `Order` の間のアソシエーションで、**子プロパティ**が**True**に設定されている場合、`Orders` という名前のプロパティが親クラスに作成されます。|
|**親プロパティ**|関連付けられている親クラスを参照する子クラスのプロパティです。 たとえば、`Customer` と `Order` の間の関連付けでは、注文に関連付けられた顧客を参照する `Customer` という名前のプロパティが `Order` クラスに作成されます。|
|**関与のプロパティ**|関連付けのプロパティを表示し、 **[関連付けエディター]** ダイアログ ボックスを再び開く**省略記号**ボタン (...) が用意されています。|
|**一意**|外部ターゲット列に一意性の制約があるかどうかを示します。|

## <a name="to-create-an-association-between-entity-classes"></a>エンティティ クラス間に関連付けを作成するには

1. 関連付けの親クラスを表すエンティティ クラスを右クリックし、 **[追加]** をポイントして、 **[関連付け]** をクリックします。

2. **[関連付けエディター]** ダイアログ ボックスで、正しい**親クラス**が選択されていることを確認します。

3. コンボ ボックスで**子クラス**を選択します。

4. クラスに関連する **[関連付けのプロパティ]** を選択します。 通常、これはデータベースで定義されている外部キー リレーションシップにマップされます。 たとえば、`Customers` と `Orders` の関連付けでは、**関連付けプロパティ**は各クラスの `CustomerID` です。

5. **[OK]** をクリックして、関連付けを作成します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラスの作成](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: 主キーを表す](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
