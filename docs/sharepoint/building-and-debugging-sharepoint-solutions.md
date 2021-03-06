---
title: ビルドと SharePoint ソリューションのデバッグ |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e91c1433fde85a9ec828a6a018bee986fdc7aa5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988134"
---
# <a name="build-and-debug-sharepoint-solutions"></a>ビルドし、SharePoint ソリューションのデバッグ
  ビルドと SharePoint ソリューションのデバッグはビルドと他の種類のプロジェクトのデバッグと同じ一般に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 このセクションのトピックでは、いくつかある相違点について説明します。

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint ソリューションのプロジェクトの出力
 アセンブリと、ソリューション パッケージを作成する SharePoint ソリューションの構築 ( *.wsp*) ファイル。 次の表では、ビルド時にこれらのファイルの場所を示します。

|ビルド項目|出力フォルダー|
|----------------|-------------------|
|アセンブリ、プログラム データベース ( *.pdb*)、および *.wsp*ファイル。|*\<ProjectName > \bin\debug*または *\<ProjectName > \bin\release*|
|SharePoint プロジェクト アイテム ファイル。|*\<プロジェクト名 > \pkg\debug*または *\<ProjectName > \pkg\release*|
|中間ファイルをビルドします。|*\<プロジェクト名 > \obj\debug*または *\<ProjectName > \obj\release*|
|パッケージの中間ファイル。|*\<プロジェクト名 > \pkgobj\debug*または *\<ProjectName > \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>SharePoint ソリューションをビルドします。
 SharePoint ソリューションをビルドするには、インストールされている SharePoint サーバーの正しいバージョンが、開発用コンピューターに必要です。 それ以外の場合、SharePoint ソリューションの構築は、その他の種類のプロジェクトをビルドする場合と同じ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 詳細については、「[方法 :SharePoint ソリューションをビルド](../sharepoint/how-to-build-sharepoint-solutions.md)します。

## <a name="debug-and-test-sharepoint-solutions"></a>デバッグし、SharePoint ソリューションのテスト
 デバッグをする前に[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]コピー、 *.wsp* SharePoint サーバーにパッケージがサイトと Web スコープの機能をアクティブにし、場合によっては、プロジェクトを開始します。 それ以外の場合は、プロジェクトを手動で開く必要があります。 詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint ソリューション](../sharepoint/troubleshooting-sharepoint-solutions.md)と[デバッグの SharePoint ソリューション](../sharepoint/debugging-sharepoint-solutions.md)します。

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>デバッグし、Azure DevOps サービス機能を使用して SharePoint ソリューションを確認します。
 単体テストや IntelliTrace などの azure DevOps サービス機能では、SharePoint ソリューションの正確に特定の問題の詳細に有効にします。 プロファイルを見つけて、SharePoint ソリューションのパフォーマンスの問題の領域を識別できます。 詳細については、次を参照してください。 [SharePoint コードのデバッグの検証および](../sharepoint/verifying-and-debugging-sharepoint-code.md)と[SharePoint アプリケーションのパフォーマンスのプロファイリング](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)します。

## <a name="security-during-the-build-process"></a>ビルド プロセス中のセキュリティ
 SharePoint のソリューションを配置またはパッケージ化する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アクセス許可を SharePoint サーバーにファイルをコピーする必要があります。 実行する必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]として昇格されたプロセスと、ユーザー アカウントが SharePoint サーバーのサイト コレクション管理者をする必要があります。 さらに、プロジェクトがサンド ボックス ソリューションまたはファーム ソリューションであるかどうかを指定する必要があります。 詳細については、次を参照してください。 [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)します。

## <a name="using-the-clean-command"></a>[クリーン] コマンドを使用します。
 SharePoint ソリューションのデバッグについては、SharePoint サーバーのインストール時に、**クリーン**コマンドでは、ソリューションはアンインストールされません。 代わりに、SharePoint 構成から機能を非アクティブ化する必要があります。

## <a name="see-also"></a>関連項目
- [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)
- [サーバー エクスプ ローラーを使用した SharePoint 接続を参照します。](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
