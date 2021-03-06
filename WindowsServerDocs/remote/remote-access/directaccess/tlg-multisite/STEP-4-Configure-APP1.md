---
title: 手順 4. の構成
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7000e80f-31b1-43c5-b51e-1469d26909e5
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 22775a3c453cf59a3dfd1d4b7e8a9522057790b4
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80308691"
---
# <a name="step-4-configure-app1"></a>手順 4. の構成

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

IPv6 の静的なアドレス指定とゲートウェイの設定を構成して、2つの企業ネットワークサブネットへのアクセスを可能にします。  
  
- 既定のゲートウェイと DNS サーバーを構成するには マルチサイト構成では、ROUTER1 コンピューターが既定のゲートウェイとして使用されます。 既定のゲートウェイを標準ゲートウェイに構成する。  
  
## <a name="to-configure-the-default-gateway-and-dns-server"></a>既定のゲートウェイと DNS サーバーを構成するには  
  
1.  サーバーマネージャーコンソールで、 **[ローカルサーバー]** をクリックし、 **[プロパティ]** 領域の **[ワイヤード (有線) イーサネット接続]** の横にあるリンクをクリックします。  
  
2.  **[ネットワーク接続]** ウィンドウで、 **[ワイヤード (イーサネット) 接続]** を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[ワイヤード (有線) イーサネット接続のプロパティ]** ダイアログボックスで、 **[インターネットプロトコルバージョン 4 (TCP/IPv4)]** をクリックし、 **[プロパティ]** をクリックします。  
  
4.  **[デフォルトゲートウェイ]** に「 **10.0.0.254**」と入力し、 **[代替 DNS サーバー]** に「 **10.2.0.1**」と入力して、[ **OK]** をクリックします。  
  
5.  **[ワイヤード (有線) イーサネット接続のプロパティ]** ダイアログボックスで、 **[インターネットプロトコルバージョン 6 (TCP/IPv6)]** をクリックし、 **[プロパティ]** をクリックします。  
  
6.  **[デフォルトゲートウェイ]** で、「 **2001: db8: 1:: fe**」と入力します。 **[代替 DNS サーバー]** に「 **2001: db8: 2:: 1**」と入力し、[ **OK]** をクリックします。  
  
7.  **[ワイヤード (有線) イーサネット接続のプロパティ]** ダイアログボックスで、 **[閉じる]** をクリックし、 **[ネットワーク接続]** ウィンドウを閉じます。  
  


