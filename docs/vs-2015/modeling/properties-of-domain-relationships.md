---
title: ドメインリレーションシップのプロパティ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95372b2bc7537e017a4eeca9b414ef054d82046d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671537"
---
# <a name="properties-of-domain-relationships"></a>ドメイン リレーションシップのプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

次の表のプロパティは、ドメインリレーションシップに関連付けられています。 ドメインリレーションシップの詳細については、「[モデル、クラス、およびリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)について」を参照してください。 これらのプロパティの使用方法の詳細については、「[ドメイン固有言語のカスタマイズと拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)」を参照してください。

|property|説明|既定|
|--------------|-----------------|-------------|
|アクセス修飾子|ドメインリレーションシップのアクセスレベル (`public` または `internal`)。|`public`|
|カスタム属性|ドメインリレーションシップから生成されるソースコードクラスに属性を追加するために使用します。|\<none>|
|2つの派生を生成します|@No__t_0 場合、基本クラスと部分クラス (オーバーライドによるカスタマイズをサポートする) の両方が生成されます。 詳細については、「[生成されたクラスのオーバーライドと拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|`False`|
|カスタムコンストラクターがある|@No__t_0 の場合、カスタムコンストラクターがソースコードで提供されていることを示します。 詳細については、「[生成されたクラスのオーバーライドと拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|`False`|
|継承修飾子|ドメインリレーションシップ (`none`、`abstract` または `sealed`) から生成されるソースコードクラスの継承の種類について説明します。|\<none>|
|重複を許可|@No__t_0 した場合、同じ2つの要素間にドメインリレーションシップの重複リンクが作成される可能性があります。|`False`|
|基本リレーションシップ|ドメインリレーションシップが派生している場合は、ドメインリレーションシップの基本関係。|\<none>|
|埋め込み|@No__t_0 の場合、ドメインリレーションシップは埋め込みリレーションシップです。 @No__t_0 の場合、リレーションシップは参照リレーションシップです。|\<both >|
|名|ドメインリレーションシップの名前。|現在の名前|
|Namespace|ドメインリレーションシップに関連付けられている名前空間。|現在の名前空間|
|ノート|ドメインリレーションシップに関連付けられている非公式のメモ。|\<none>|
|説明|コードをドキュメント化するために使用される説明。生成されたデザイナーの UI で使用されます。|\<none>|
|[表示名]|ドメインリレーションシップの生成されたデザイナーに表示される名前。|\<none>|
|ヘルプ キーワード|ドメインリレーションシップの F1 ヘルプのインデックスを作成するために使用される省略可能なキーワードです。|\<none>|

## <a name="see-also"></a>参照
 [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
