---
title: Windows Server Essentials の移行先サーバー 1 でフォルダー リダイレクトを有効にする
description: Windows Server Essentials の使用方法について説明します。
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
H1: Windows Server Essentials の移行先サーバーでフォルダーリダイレクトを有効にする
ms.assetid: f67d195e-36f6-495a-8361-6d5faa889441
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 301224256c196b9788e80d38112ed94a6073e054
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319005"
---
# <a name="enable-folder-redirection-on-the-windows-server-essentials-destination-server1"></a>Windows Server Essentials の移行先サーバー 1 でフォルダー リダイレクトを有効にする

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

移行元サーバーでフォルダー リダイレクトが有効になっている場合、このタスクを実行できます。  
  
 まず、Windows Server Essentials ダッシュボードを使用して、移行先サーバーでフォルダーリダイレクトを有効にします。 次に、古いフォルダー リダイレクト グループ ポリシーの設定を削除します。  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>移行先サーバーでフォルダー リダイレクトを有効にするには  
  
1.  移行先サーバーで、Windows Server Essentials ダッシュボードを開きます。  
  
2.  ナビゲーション バーで、 **[デバイス]** をクリックします。  
  
3.  **[デバイスのタスク]** ウィンドウで、 **[グループ ポリシーの実装]** をクリックします。  
  
4.  **[フォルダー リダイレクト グループ ポリシーを有効にする]** ページで、リダイレクトするフォルダーを選択し、 **[次へ]** をクリックします。  
  
5.  **[セキュリティ ポリシー設定を有効にする]** ページで、 **[完了]** をクリックします。  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>古いフォルダー リダイレクト グループ ポリシーの設定を削除するには  
  
1. 移行先サーバーで、 **[グループ ポリシーの管理]** 管理ツールを開きます。  
  
2. **グループポリシー管理** で、 **フォレスト:** <em>ネットワークドメイン名</em>、**ドメイン**、*ネットワークドメイン名* の順に展開し、**グループポリシーオブジェクト** を展開します。  
  
3. **[W7PVP フォルダー リダイレクト]** を右クリックし、 **[削除]** をクリックします。  
  
4. 警告を読み、 **[はい]** をクリックします。  
  
5. **[グループ ポリシーの管理]** を閉じます。  
  
   フォルダー リダイレクトの変更を適用するには、ネットワーク ユーザーはコンピューターからログオフした後、ログオンし直す必要があります。 これにより、リダイレクトされるすべてのフォルダーが移行先サーバーに転送されます。
