---
title: DirectAccess クラスター/NLB テスト ラボの構成手順
description: このトピックは、「windows Server 2016 用 Windows NLB を使用するクラスターでの DirectAccess のデモンストレーション」のテストラボガイドに含まれています。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e508d3ee-ffa6-463f-a3dd-9e35e745c005
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 2ea4658df75b7e290d66751a1373181f60f05f4e
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80310737"
---
# <a name="steps-for-configuring-the-directaccess-cluster-nlb-test-lab"></a>DirectAccess クラスター/NLB テスト ラボの構成手順

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

次の手順では、リモートアクセスインフラストラクチャを構成し、リモートアクセスサーバーとクライアントを構成し、インターネットおよび Homenet サブネットから DirectAccess 接続をテストする方法について説明します。  
  
このテストラボガイドでは、次の手順を実行して、ネットワーク負荷分散 (NLB) が有効になっているリモートアクセスクラスターを構築します。  
  
-   [手順 1 DirectAccess の構成を完了](STEP-1-Complete-the-DirectAccess-Configuration.md)します。 [「テストラボガイド: 混在 IPv4 と IPv6 を使用した DirectAccess シングルサーバーセットアップのデモンストレーション](https://go.microsoft.com/fwlink/p/?LinkId=237004)」に記載されているすべての手順を完了します。  
  
-   [手順 2: EDGE1 を構成](STEP-2-Configure-EDGE1.md)します。 負荷分散のために EDGE1 でリモートアクセスの役割を構成します。  
  
-   [手順 3: EDGE2 をインストールして構成](STEP-3-Install-and-Configure-EDGE2.md)します。 EDGE2 は、リモートアクセスクラスターの2番目のリモートアクセスサーバーとして機能します。  
  
-   [手順 4: ネットワーク負荷分散リモートアクセスクラスターを作成](STEP-4-Create-the-Network-Load-Balanced-Remote-Access-Cluster.md)する-EDGE1 は、リモートアクセスクラスターの最初のサーバーとして構成されます。 EDGE2 がクラスターに参加し、NLB がクラスター用に構成されています。  
  
-   [手順 5: インターネットおよびクラスターを使用して、DirectAccess 接続をテスト](STEP-5-Test-DirectAccess-Connectivity-from-the-Internet-and-Through-the-Cluster.md)します。 NLB とクラスターの構成が完了したら、負荷分散されたクラスターを使用して DirectAccess クライアントの接続をテストできます。  
  
-   [手順 6: NAT デバイスの背後からの DirectAccess クライアント接続をテスト](STEP-6-Test-DirectAccess-Client-Connectivity-from-Behind-a-NAT-Device.md)します。 NAT デバイスの背後にあるクライアントコンピューターを移動して、ホームルーターの背後からの DirectAccess クライアント接続のテストをシミュレートします。  
  
-   [手順 7: 企業ネットワークに戻るときに接続をテストする](STEP-7-Test-Connectivity-When-Returning-to-the-Corpnet.md) 企業ネットワークに戻るときに、クライアントコンピューターが会社のリソースに引き続きアクセスできることを確認します。  
  
-   [手順 8: 構成のスナップショットを設定](da-cluster-nlb-s8-snapshot.md)します。 テストラボを完了したら、作業中のリモートアクセス NLB クラスターのスナップショットを作成して、後で追加のシナリオをテストすることができるようにします。  
  


