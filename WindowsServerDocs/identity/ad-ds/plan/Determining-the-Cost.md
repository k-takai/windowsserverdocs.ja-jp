---
ms.assetid: e3ea1f67-60d4-4566-b24c-37faa95c3b2a
title: コストを決定する
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 0ce7acddbfa9f7536f3d5a190c6968ea0d8cf6b3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408870"
---
# <a name="determining-the-cost"></a>コストを決定する

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

コストの値をサイトリンクに割り当てて、高価な接続での安価な接続を優先します。 ドメインコントローラーロケーター (DCLocator) や分散ファイルシステム名前空間 (DFSN) などの特定のアプリケーションやサービスでは、コスト情報を使用して最も近いリソースを特定することもできます。 サイトリンクコストを使用して、指定したドメインのドメインコントローラーがそのサイトに存在しない場合に、1つのサイトのクライアントがどのドメインコントローラーに接続しているかを判断できます。 クライアントは、割り当てられているコストが最も低いサイトリンクを使用して、ドメインコントローラーと通信します。  
  
コストの値は、サイト全体に対して定義することをお勧めします。 コストは、通常、リンクの合計帯域幅だけでなく、リンクの可用性、待機時間、および金銭的コストにも基づいています。  
  
サイトリンクに配置するコストを決定するには、各サイトリンクの接続速度を文書化します。 特定した接続速度の詳細については、「[ネットワーク情報の収集](../../ad-ds/plan/Collecting-Network-Information.md)」の「地理的な場所と通信リンク」 (DSSTOPO_1) ワークシートを参照してください。  
  
次の表に、さまざまな種類のネットワークの速度を示します。  
  
|ネットワークの種類|速度|  
|----------------|---------|  
|非常に遅い|56キロビット/秒 (Kbps)|  
|スロー (低速)|64 Kbps|  
|統合サービスデジタルネットワーク (ISDN)|64 kbps または 128 Kbps|  
|フレームリレー|変動率 (通常は 56 Kbps と 1.5 mbps (Mbps))|  
|T1|1.5 Mbps|  
|T3|45 Mbps|  
|10BaseT|10 Mbps|  
|非同期転送モード (ATM)|変動率 (通常は 155 Mbps と 622 Mbps)|  
|100BaseT|100 Mbps|  
|ギガビットイーサネット|1ギガビット/秒 (Gbps)|  
  
次の表を使用して、ワイドエリアネットワーク速度 (WAN) リンク速度に基づいて各サイトリンクのコストを計算します。 表に記載されていない WAN リンクの速度の場合は、1024を、使用可能な帯域幅のログ (Kbps 単位) で割って相対的なコスト係数を計算できます。  
  
|使用可能な帯域幅 (Kbps)|コスト|  
|--------------------------------|--------|  
|9.6|1042|  
|19.2|798|  
|38.4|644|  
|56|586|  
|64|567|  
|128|486|  
|256|425|  
|512|378|  
|1,024|340|  
|2048|309|  
|4,096|283|  
  
これらのコストには、ネットワークリンク間の信頼性の違いは反映されません。 障害が発生しやすいネットワークリンクのコストを高く設定して、レプリケーションのためにこれらのリンクを使用する必要がないようにします。 サイトリンクのコストを高く設定すると、サイトリンクに障害が発生した場合にレプリケーションのフェールオーバーを制御できます。  
  


