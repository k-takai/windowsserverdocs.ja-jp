---
title: 証明書ベースの認証が構成されていますが、指定された証明書がレプリカサーバーまたはフェールオーバークラスターノードにインストールされていません
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 4cabbce3-9367-4ddc-a108-1e5e1ab2bcff
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 0b107a4760cc3470c7f80d53feef00a2f8f789c5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365200"
---
# <a name="certificate-based-authentication-is-configured-but-the-specified-certificate-is-not-installed-on-the-replica-server-or-failover-cluster-nodes"></a>証明書ベースの認証が構成されていますが、指定された証明書がレプリカサーバーまたはフェールオーバークラスターノードにインストールされていません

>適用先:Windows Server 2016


  
*ベストプラクティスとスキャンの詳細については、「ベストプラクティスアナライザー」を参照してください* [](https://go.microsoft.com/fwlink/?LinkId=122786)。  
  
|プロパティ|詳細|  
|-|-|  
|**オペレーティング システム**|Windows Server 2016|  
|**製品/機能**|Hyper-V|  
|**順**|Error|  
|**カテゴリ**|構成|  

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題  
  
*証明書ベースのレプリケーションを提供するために Hyper-v レプリカが構成されているセキュリティ証明書が、レプリカサーバー (またはフェールオーバークラスターノード) にインストールされていません。*  
  
## <a name="impact"></a>影響  
  
*In のフェールオーバーが発生した場合、または別のノードに移動した場合、新しいノードに適切な証明書がインストールされていなければ、Hyper-v レプリケーションは一時停止します。これは次のノードに影響します:*  
  
\< ノードの一覧 >  
  
## <a name="resolution"></a>解決方法  
  
*構成した証明書をレプリカサーバー (およびフェールオーバークラスター内のすべての関連ノード (存在する場合) にインストールします。*  
  


