---
title: '&lt;postAction&gt;要素 (Visual Studio での Office 開発)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53cf47ef9a78ebb54c377e19b4f7fbad444bbfcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976529"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt;要素 (Visual Studio での Office 開発)
  `postAction` 名前空間の `vstav3` 要素には、配置後アクションに関連付ける `entrypoint` 要素とすべての `postActionData` 要素を格納します。これらの要素は、Office ソリューションのインストール後に実行されます。

## <a name="syntax"></a>構文

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>要素と属性
 `postAction` 要素は省略可能であり、 `vstav3` 名前空間にあります。 アプリケーション マニフェストには、配置後アクションごとに `postAction` 要素を 1 つ定義します。

 `postAction`要素に属性がありません。

 `postAction` には、次の要素があります。

### <a name="entrypoint"></a>entrypoint
 省略可能です。 ロール、`entryPoint`内の要素、`vstav3`で名前空間が定義されている[ &#60;entryPoints&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)します。

### <a name="postactiondata"></a>postActionData
 省略可能です。 ロール、`postActionData`内の要素、`vstav3`で名前空間が定義されている[ &#60;postActionData&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)します。

## <a name="post-deployment-action-example"></a>配置後アクションの例

### <a name="description"></a>説明
 次のコード例は、 `postAction` を使用して配置する Office ソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)
