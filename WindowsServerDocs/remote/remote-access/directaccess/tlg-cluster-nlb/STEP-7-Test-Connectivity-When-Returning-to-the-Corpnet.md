---
title: 手順7企業ネットワークに戻るときに接続をテストする
description: このトピックは、「windows Server 2016 用 Windows NLB を使用するクラスターでの DirectAccess のデモンストレーション」のテストラボガイドに含まれています。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a7252d0-6db8-4a9d-98ee-75082ecd2929
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 491533ae5d141de4ab4f15126d8977cf15c8f7f4
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314687"
---
# <a name="step-7-test-connectivity-when-returning-to-the-corpnet"></a>手順7企業ネットワークに戻るときに接続をテストする

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

多くのユーザーがリモートの場所と企業ネットワークの間を移動するため、構成を変更しなくてもリソースにアクセスできることを企業ネットワークに戻すことが重要です。 リモートアクセスを使用すると、DirectAccess クライアントが企業ネットワークに戻ったときに、ネットワークロケーションサーバーに接続できるようになります。 ネットワークロケーションサーバーへの HTTPS 接続が正常に確立されると、DirectAccess クライアントは DirectAccess クライアントの構成を無効にし、企業ネットワークへの直接接続を使用します。  
  
### <a name="test-connectivity-on-client1"></a>CLIENT1 での接続テスト  
  
1. CLIENT1 をシャットダウンしてから、CLIENT1 サブネットまたは仮想スイッチから CLIENT1 を取り外し、企業ネットワークのサブネットまたは仮想スイッチに接続します。 CLIENT1 をオンにして、Corp\user1 としてログオンします。  
  
2. 管理者特権の Windows PowerShell ウィンドウを開き、「 **ipconfig/all**」と入力して、enter キーを押します。 出力には、CLIENT1 にローカル IP アドレスがあり、アクティブな6to4、Teredo、または ip-https トンネルがないことが示されます。  
  
3. APP2 上のネットワーク共有への接続をテストします。 **スタート**画面で、「<strong>\\\APP2\Files</strong>」と入力し、enter キーを押します。 そのフォルダー内のファイルを開くことができます。  
  


