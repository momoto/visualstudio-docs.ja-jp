---
title: ClickOnce の更新方法の選択 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8215b8e0955b79224341d5d43b51a473740f5fe5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442334"
---
# <a name="choosing-a-clickonce-update-strategy"></a>ClickOnce の更新方法の選択
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] では、アプリケーションを自動的に更新できます。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションは、配置マニフェスト ファイルを定期的に読み取り、アプリケーションに対する更新が利用可能かどうかを確認します。 利用可能であれば、アプリケーションの新しいバージョンがダウンロードされて実行されます。 効率性を高めるために、変更されたファイルだけがダウンロードされます。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションのデザイン時に、アプリケーションが利用可能な更新プログラムをチェックする際に使用する方法を決定する必要があります。 使用できる基本的な方法は、アプリケーションの起動時に更新プログラムをチェックする方法、アプリケーションの起動後に更新プログラムをチェックする方法 (バックグラウンド スレッドで実行)、更新用のユーザー インターフェイスを提供する方法の 3 つです。  
  
 また、アプリケーションが更新プログラムをチェックする頻度を決定でき、更新を必須にすることもできます。  
  
> [!NOTE]
> アプリケーションの更新には、ネットワーク接続が必要です。 ネットワーク接続されていない場合、選択した更新方法に関係なく、アプリケーションは更新プログラムをチェックせずに実行されます。  
  
> [!NOTE]
> .NET Framework 2.0 および .NET Framework 3.0 で、アプリケーションの起動の前後または <xref:System.Deployment.Application> の API を使用する前後に更新プログラムがあるかどうかをチェックする場合は、配置マニフェストで `deploymentProvider` を設定する必要があります。 `deploymentProvider` 要素は、Visual Studio の **[発行]** タブの **[更新]** ダイアログ ボックスにある **[更新の場所]** に対応します。この規則は .NET Framework 3.5 で緩和されています。 詳細については、次を参照してください。 [ClickOnce アプリケーションのテストの展開および Resigning なしの実稼働サーバー](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)します。  
  
## <a name="checking-for-updates-after-application-startup"></a>アプリケーション起動後の更新プログラムのチェック  
 この方法を使用した場合、アプリケーションは、実行中にバックグラウンドで配置マニフェスト ファイルの検索と読み取りを試みます。 更新が利用可能な場合は、ユーザーが次回アプリケーションを実行したときに、更新プログラムをダウンロードしてインストールするかどうかを確認するプロンプトが表示されます。  
  
 この方法は、低帯域幅のネットワーク接続や、ダウンロードに時間を要する可能性のあるサイズの大きなアプリケーションに最も適しています。  
  
 この更新方法を有効にするには、**[アプリケーションの更新]** ダイアログ ボックスの **[アプリケーションの更新プログラムを確認する方法を選択してください]** セクションにある **[アプリケーションの開始後に行う]** をクリックします。 さらに、**[アプリケーションの更新プログラムの確認を実行する頻度を指定してください]** で更新間隔を指定します。  
  
 これは、次のように配置マニフェストで **Update** 要素を変更することと同じです。  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>アプリケーション起動前の更新プログラムのチェック  
 既定の方法では、アプリケーションが起動される前に、配置マニフェストの検索と読み取りが試みられます。 この方法を使用した場合、ユーザーがアプリケーションを起動するたびに、アプリケーションは配置マニフェスト ファイルの検索と読み取りを試みます。 更新プログラムが利用可能な場合は、更新プログラムがダウンロードされ、起動されます。それ以外の場合は、アプリケーションの既存のバージョンが起動されます。  
  
 この方法は、高帯域幅のネットワーク接続に最も適しています。低帯域幅の接続では、アプリケーション起動時の遅延が容認できないほど長くなる可能性があります。  
  
 この更新方法を有効にするには、**[アプリケーションの更新]** ダイアログ ボックスの **[アプリケーションの更新プログラムを確認する方法を選択してください]** セクションにある **[アプリケーションの開始前に行う]** をクリックします。  
  
 これは、次のように配置マニフェストで **Update** 要素を変更することと同じです。  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>更新の必須化  
 アプリケーションの最新バージョンを実行するようユーザーに要求することが必要な場合があります。 たとえば、Web サービスなどの外部リソースに変更を加えたことで、旧バージョンのアプリケーションが適切に動作できなくなるような場合です。 この場合、更新を必須としてマークし、ユーザーが旧バージョンを実行するのを防ぎます。  
  
> [!NOTE]
> 他の更新方法を使用して更新を要求することもできますが、古いバージョンを確実に実行できないようにするのは、**[アプリケーションの開始前に行う]** をオンにする方法だけです。 起動時に必須の更新が検出された場合、ユーザーは更新を受け入れるか、アプリケーションを終了する必要があります。  
  
 更新を必須としてマークするには、**[アプリケーションの更新]** ダイアログ ボックスで **[このアプリケーションに最低限必要なバージョンを指定してください]** をクリックし、発行バージョン (**[メジャー]**、**[マイナー]**、**[ビルド]**、**[リビジョン]**) を指定することで、インストール可能なアプリケーションの最も低いバージョン番号を指定します。  
  
 これは、次のように配置マニフェストの **Deployment** 要素の **minimumRequiredVersion** 属性を設定することと同じです。  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>更新間隔の指定  
 アプリケーションが更新プログラムをチェックする頻度を指定できます。 そのためには、前の「アプリケーション起動後の更新プログラムのチェック」で説明したように、アプリケーションが起動後に更新プログラムをチェックするように指定します。  
  
 更新間隔を指定するには、**[アプリケーションの更新]** ダイアログ ボックスの **[アプリケーションの更新プログラムの確認を実行する頻度を指定してください]** プロパティを設定します。  
  
 これは、配置マニフェストで **Update** 要素の **maximumAge** 属性と **unit** 属性を設定することと同じです。  
  
 たとえば、アプリケーションを実行するたびにチェックしたり、週に 1 回または月に 1 回チェックしたりできます。 指定した時期にネットワーク接続されていない場合は、アプリケーションを次回実行したときに、更新プログラムのチェックが実行されます。  
  
## <a name="providing-a-user-interface-for-updates"></a>更新プログラム用ユーザー インターフェイスの提供  
 この方法を使用する場合、アプリケーション開発者は、アプリケーションが更新プログラムをチェックする場所と頻度をユーザーが選択できるようにするユーザー インターフェイスを提供します。 たとえば、[更新を今すぐ確認] コマンドや、別の更新間隔を選択できる [更新の設定] ダイアログ ボックスなどを提供できます。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 配置 API には、独自の更新用ユーザー インターフェイスをプログラミングするためのフレームワークが用意されています。 詳細については、「<xref:System.Deployment.Application>」を参照してください。  
  
 アプリケーションが配置 API を使用して自身の更新ロジックを制御する場合、次の「更新プログラムのチェックのブロッキング」で説明されているように更新プログラムのチェックをブロックする必要があります。  
  
 この方法は、ユーザーごとに異なる更新方法が必要な場合に最も適しています。  
  
## <a name="blocking-update-checking"></a>更新プログラムのチェックのブロッキング  
 アプリケーションが更新プログラムをチェックしないようにすることもできます。 たとえば、更新されることのない単純なアプリケーションがあるが、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] の配置によって提供されるインストールの容易さは利用したい場合があります。  
  
 アプリケーションが配置 API を使用して自身の更新を実行する場合も、更新プログラムのチェックをブロックする必要があります。前の「更新用ユーザー インターフェイスの提供」を参照してください。  
  
 更新プログラムのチェックをブロックするには、[アプリケーションの更新] ダイアログ ボックスの **[アプリケーションの更新プログラムを確認する]** チェック ボックスをオフにします。  
  
 配置マニフェストから `<Subscription>` タグを削除することにより、更新プログラムのチェックをブロックすることもできます。  
  
## <a name="permission-elevation-and-updates"></a>アクセス許可の昇格と更新  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションの新しいバージョンが、実行の際に以前のバージョンよりも高い信頼レベルを必要とする場合、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] はユーザーに対し、この高い信頼レベルをアプリケーションに付与するかどうかを確認します。 ユーザーが高い信頼レベルの付与を拒否した場合、更新プログラムはインストールされません。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] で、次回の起動時にアプリケーションを再インストールするように求めるメッセージが表示されます。 その時点でユーザーがより高い信頼レベルの付与を拒否し、更新が必須とマークされていない場合は、アプリケーションの古いバージョンが実行されます。 ただし、更新が必須である場合は、ユーザーがより高い信頼レベルを受け入れるまで、アプリケーションは実行されません。  
  
 信頼されたアプリケーションの配置を使用する場合は、信頼レベルの要求が行われません。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application>   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce がアプリケーションの更新プログラムを実行する方法](../deployment/how-clickonce-performs-application-updates.md)   
 [方法: ClickOnce アプリケーションの更新プログラムを管理する](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
