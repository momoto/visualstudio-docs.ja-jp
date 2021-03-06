---
title: '方法: プログラム コード内のファイルからモデルを開く'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d39543a388c112cf13a5841e4fe825717597d5c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661176"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>方法: プログラム コード内のファイルからモデルを開く

DSL モデルは任意のアプリケーションで開くことができます。

この目的には、Visual Studio 拡張機能から ModelBus を使用できます。 ModelBus には、モデル内のモデルまたは要素を参照したり、モデルが移動された場合にそのモデルを検索したりするための標準的なメカニズムが用意されています。 詳細については、「 [Visual Studio Modelbus を使用](../modeling/integrating-models-by-using-visual-studio-modelbus.md)したモデルの統合」を参照してください。

## <a name="target-framework"></a>[対象とする Framework]

アプリケーションプロジェクトの**ターゲットフレームワーク**を .NET Framework 4 以降に設定します。

1. DSL モデルを読み取るアプリケーションの Visual Studio プロジェクトを開きます。

2. **ソリューションエクスプローラー**で、プロジェクトを右クリックし、 **[プロパティ]** をクリックします。

3. プロジェクトのプロパティウィンドウの **[アプリケーション]** タブで、 **[ターゲットフレームワーク]** フィールドを **.NET Framework 4** (またはそれ以降) に設定します。

> [!NOTE]
> ターゲットフレームワークを **.NET Framework 4 クライアントプロファイル**にすることはできません。

## <a name="references"></a>関連項目

次の参照を Visual Studio アプリケーションプロジェクトに追加します。

- `Microsoft.VisualStudio.Modeling.Sdk.11.0`

  - **[参照の追加]** ダイアログボックスの **[.net]** タブにこれが表示されない場合は、 **[参照]** タブをクリックし、`%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\` に移動します。

- Dsl アセンブリ。 DSL プロジェクトの bin フォルダーの下にあります。 この名前は、通常、*会社*の形式です。*YourProject* `.Dsl.dll`。

## <a name="important-classes-in-the-dsl"></a>DSL の重要なクラス

DSL を読み取るコードを記述する前に、DSL によって生成されたいくつかのクラスの名前がわかっている必要があります。 DSL ソリューションで、 **dsl**プロジェクトを開き、[作成された**コード**] フォルダーを探します。 または、プロジェクト**参照**で dsl アセンブリをダブルクリックし、**オブジェクトブラウザー**で dsl 名前空間を開きます。

次のクラスを識別する必要があります。

- 自分の*Dslrootclass* -`DslDefinition.dsl` 内のルートクラスの名前です。

- *Dslname* `SerializationHelper`-このクラスは、DSL プロジェクトの `SerializationHelper.cs` で定義されています。

- *Dslname* `DomainModel`-このクラスは、DSL プロジェクトの `DomainModel.cs` で定義されています。

## <a name="read-from-a-file"></a>ファイルのデータを読み取ります。

次の例は、重要なクラスが次のような DSL を読み取るように設計されています。

- FamilyTreeModel

- FamilyTreeSerializationHelper

- FamilyTreeDomainModel

この DSL のもう1つのドメインクラスは Person です。

```csharp
using System;
using Microsoft.VisualStudio.Modeling;
using Company.FamilyTree; // Your DSL namespace

namespace StandaloneReadDslConsole
{ class Program
  { static void Main(string[] args)
    {
      // The path of a DSL model file:
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";
      // Set up the Store to read your type of model:
      Store store = new Store(
        typeof(Company.FamilyTree.FamilyTreeDomainModel));
      // The Model type generated by the DSL:
      FamilyTreeModel familyTree;
      // All Store changes must be in a Transaction:
      using (Transaction t =
        store.TransactionManager.BeginTransaction("Load model"))
      {
        familyTree =
           FamilyTreeSerializationHelper.Instance.
              LoadModel(store, dslModel, null, null, null);
        t.Commit(); // Don't forget this!
      }
      // Now we can read the model:
      foreach (Person p in familyTree.People)
      {
        Console.WriteLine(p.Name);
        foreach (Person child in p.Children)
        {
          Console.WriteLine("    " + child.Name);
        }
} } } }
```

## <a name="save-to-a-file"></a>ファイルに保存する

前のコードに追加された次のコードにより、モデルが変更され、ファイルに保存されます。

```csharp
using (Transaction t =
  store.TransactionManager.BeginTransaction("update model"))
{
  // Create a new model element:
  Person p = new Person(store);
  // Set its embedding relationship:
  p.FamilyTreeModel = familyTree;
  // - same as: familyTree.People.Add(p);
  // Set its properties:
  p.Name = "Edward VI";
  t.Commit(); // Don't forget this!
}
// Save the model:
try
{
  SerializationResult result = new SerializationResult();
  FamilyTreeSerializationHelper.Instance
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");
  // Report any error:
  if (result.Failed)
  {
    foreach (SerializationMessage message in result)
    {
      Console.WriteLine(message);
    }
  }
}
catch (System.IO.IOException ex)
{ ... }
```
