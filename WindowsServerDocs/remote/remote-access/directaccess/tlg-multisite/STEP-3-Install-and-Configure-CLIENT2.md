---
title: 手順 3. のインストールと構成
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f009fdd1-94e6-4ccb-8c6e-609a5394db53
ms.author: lizross
author: eross-msft
ms.openlocfilehash: ad09bdef0fba9f8114a09e3ddadb8237be2b7d9f
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80308705"
---
# <a name="step-3-install-and-configure-client2"></a>手順 3. のインストールと構成

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

"手順 1" は、windows Server 2016 サーバーで実行されているリモートアクセスの下位互換性を示すために使用される Windows 7&reg; コンピューターです。  
  
1. オペレーティングシステムをインストールするには、 Windows&reg; 7 Enterprise または Windows&reg; 7 Ultimate にインストールします。  
  
2. を CORP ドメインに参加させます。 Corp.contoso.com ドメインには、その後に結合します。  
  
## <a name="to-install-the-operating-system-on-client2"></a>コンピューターにオペレーティングシステムをインストールするには  
  
1.  Windows 7 のインストールを開始します。  
  
2.  ユーザー名の入力を求めるメッセージが表示されたら、「 **User1**」と入力します。 コンピューター名の入力を求めるメッセージが表示さ**れたら**、「」と入力します。  
  
3.  パスワードの入力を求められたら、強力なパスワードを2回入力します。  
  
4.  保護設定を確認するメッセージが表示されたら、 **[推奨設定を使用する]** をクリックします。  
  
5.  コンピューターの現在の場所を確認するメッセージが表示されたら、[**ネットワークを使用**する] をクリックします。  
  
6.  このネットワークをインターネットにアクセスできるネットワークに接続し、Windows Update を実行して Windows 7 の最新の更新プログラムをインストールしてから、インターネットから切断します。  
  
7.  その後、企業ネットワークサブネットに接続します。  
  
## <a name="user-account-control"></a>ユーザーアカウント制御  
Windows 7 オペレーティングシステムを構成する場合は、一部のタスクについて、 **[ユーザーアカウント制御]** (UAC) ダイアログボックスの **[続行]** をクリックする必要があります。 いくつかの構成タスクでは、UAC の承認が必要です。 メッセージが表示されたら、 **[続行]** をクリックして、これらの変更を承認します。  
  
## <a name="to-join-client2-to-the-corp-domain"></a>すべての会社のドメインに追加するには  
  
1.  **[スタート]** ボタンをクリックし、 **[コンピューター]** を右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[システム]** ページの **[コンピューター名、ドメイン、およびワークグループの設定]** 領域で、設定の **[変更]** をクリックします。  
  
3.  **[システムのプロパティ]** ダイアログ ボックスの **[コンピューター名]** タブで **[変更]** をクリックします。  
  
4.  **[コンピューター名/ドメイン名の変更]** ダイアログボックスで、 **[ドメイン]** をクリックし、「 **corp.contoso.com**」と入力して、[ **OK]** をクリックします。  
  
5.  ユーザー名とパスワードの入力を求めるメッセージが表示されたら、User1 ドメインアカウントのユーザー名とパスワードを入力し、[ **OK]** をクリックします。  
  
6.  corp.contoso.com ドメインへの参加を知らせるダイアログ ボックスが表示されたら、 **[OK]** をクリックします。  
  
7.  コンピューターを再起動するかどうかを確認するダイアログボックスが表示されたら、 **[OK]** をクリックします。  
  
8.  **[システムのプロパティ]** ダイアログボックスで **[閉じる]** をクリックすると、コンピューターの再起動を求めるダイアログが表示されたら、 **[今すぐ再起動]** をクリックします。  
  
9. コンピューターが再起動したら、Corp\user1 としてログオンします。
