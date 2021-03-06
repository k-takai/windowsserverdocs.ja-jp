---
title: リモートで管理されるサーバー用のサーバー回復 DVD の作成
description: Windows Server Essentials の使用方法について説明します。
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6141fa69-5952-4e3c-a868-40ef3f4badd2
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a9b571c2d3e5d531d8c923741500c72675022adc
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80312191"
---
# <a name="create-a-server-recovery-dvd-for-remotely-administered-servers"></a>リモートで管理されるサーバー用のサーバー回復 DVD の作成

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="create-a-server-recovery-dvd-for-remotely-administered-servers"></a><a name="BKMK_HeadlessRecovery"></a>リモートで管理するサーバー用のサーバー回復 DVD を作成する  
 工場出荷時のリセットとサーバー回復には 2 つのモデルがあり、これらは顧客に納入したハードウェアによって異なります。  
  
 **リモートで管理するサーバー**  
  
 このサーバー回復オプションでは、同じネットワーク上のクライアント コンピューターからプロセスを実行する必要があります。 工場出荷時のリセットでは、ハードウェア固有のイメージをサーバーと共に出荷する必要があるため、パートナーはサーバー回復 DVD を作成する必要があります。  
  
 **ローカルで管理するサーバー**  
  
 これは従来のモデルで、サーバーはサーバー コンソールで管理されます。 回復を実行するためにサーバー インストール メディアを使用します。 このためには、サーバーには DVD リーダーに加え、ビデオ出力を表示可能な機能を搭載して出荷する必要があります。 顧客はこのサーバー インストール メディアから起動し、適切な回復方法を選択します。 ローカルで管理されているサーバーの場合、サーバー回復 DVD を作成する必要はありません。  
  
> [!NOTE]
>  ローカルで管理されているサーバー モデルの場合、顧客は新しいインストールを実行することで、工場出荷時に戻せる場合もあります。 ただし、パートナーのカスタマイズは失われます。  
  
 サーバーの回復には 2 つの種類があります。  
  
 **工場出荷時の設定へのリセット**  
  
 この回復では、サーバーは工場出荷時の元の状態に戻されます。 工場出荷時のリセットに続いて、最初にサーバーをオンにしたときと同様にサーバーの初期構成を実行するよう求められます。すべての設定とカスタマイズは失われます。 これは、Day 0 とも呼ばれます。 工場出荷時のリセットでは、ハードウェア固有のイメージをサーバーと共に出荷する必要があるため、パートナーはサーバー回復 DVD を作成する必要があります。  
  
 **ベアメタル復元**  
  
 この回復では、サーバーのバックアップを構成済みで、サーバーの障害発生前に少なくとも一度サーバーのバックアップが正常に完了していることが前提となります。 ベアメタル復元 (BMR) では、前のサーバー バックアップからのシステムとブート ドライブの復元のみがサポートされます。  
  
 BMR の後、サーバーは復元に使用されるバックアップ時の状態に戻ります。 これは通常、最新のバックアップですが、場合によっては、より古いバックアップになる可能性があります。 データの回復は、ファイルおよびフォルダーの復元ウィザードを使用してシステムを復元した後に実行されます。 BMR ではすべての設定と構成が元に戻りますが、工場出荷時のリセットではサーバーが Day 0 状態に戻るため、BMR が推奨されるサーバーの回復方法です。  
  
### <a name="remotely-administered-server-recovery"></a>リモートで管理されるサーバーの回復  
 ここでは、パートナーが実行する必要があるカスタマイズと、各サーバーと共に出荷する必要がある最終メディアについて説明します。 詳細な説明に入る前に、カスタマー エクスペリエンスについて考えてみましょう。  
  
 このシナリオでは、顧客 "され s サーバーは動作しなくなりました。 この原因としては、ウイルス、ハード ディスク障害、またはその他の原因が考えられます。 顧客は、サーバー回復 DVD をサーバーと同じネットワークにあるクライアント コンピューターに挿入します。 サーバー回復アプリケーションでは、次の 3 つの手順を通じてこのサーバーを回復します。  
  
1.  サーバーを回復モードで起動するために使用されるブート可能な USB フラッシュ ドライブを作成します。 この USB フラッシュ ドライブには、8 GB 以上の容量が必要です。  
  
2.  現在回復モードになっているサーバーを検出します。  
  
3.  顧客が工場出荷時のリセットまたはベアメタル復元を選択して、サーバーを稼働状態に戻せるようにします。  
  
### <a name="steps-for-creating-a-server-recovery-dvd-for-multiple-language-support"></a>複数の言語サポート用のサーバー回復 DVD の作成手順  
 サーバー回復 DVD を作成するには主に 6 つの手順があります。  
  
1.  [OptionalWinPE を更新する](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_Updating)  
  
2.  [出荷時のリセットイメージと XML ファイルの収集](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_Collecting)  
  
3.  [サーバー回復 DVD の作成](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_Creating)  
  
4.  [ウィザードをカスタマイズする](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_Customizing)  
  
5.  [ISO ファイルを作成する](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_CreatingISO)  
  
6.  [回復 DVD のテスト](Create-a-Server-Recovery-DVD-for-Remotely-Administered-Servers.md#BKMK_Testing)  
  
####  <a name="step-1-optional-update-winpe"></a><a name="BKMK_Updating"></a>手順 1: (省略可能) WinPE を更新する  
 ADK には、カスタマイズする Windows PE のコピーが含まれます。 このイメージを起動すると、クライアント回復アプリケーションが回復モードのサーバーに接続するために使用するビーコンが自動的に起動されます。  
  
 Windows PE は、ネットワーク ドライバーやディスク コントローラー ドライバーなどのハードウェア固有のドライバーを追加して、さらにカスタマイズする必要があります。 WinPE からの起動後、システム上のハード ディスクが認識可能であって、ネットワークが動作している必要があります。  
  
####  <a name="step-2-collect-the-factory-reset-images-and-xml-files"></a><a name="BKMK_Collecting"></a>手順 2: 出荷時の設定にリセットされたイメージと XML ファイルを収集する  
 サーバーを工場出荷時の既定の設定にリセットするには、次の 2 つのイメージをキャプチャする必要があります。  
  
- システム ドライブ イメージ  
  
- システムの予約されたパーティション  
  
  これらのイメージをキャプチャするために、GenDiskXML.exe ツールが用意されています。 GenDiskXML.exe は、disk.xml という名前のファイルも収集します。このファイルは、ディスク構成を再作成するために、回復プロセスで使用されます。  
  
1.  Sysprep に続いて、64 ビット版の Windows PE を使用してシステムを再起動します。  
  
2.  .xml ファイルと .wim ファイルを外部ソースに出力するには、 `GenDiskXML /outputdir:<path>` を実行して、.xml ファイルと .wim ファイルを任意の外部ソースに出力します。 これらのファイルは、次の手順で DVD に追加されます。  
  
    > [!NOTE]
    >  FAT32 の場合、1 ファイルのサイズが 4 GB 未満でなければならないため、システムの .wim ファイルが分割されます。 このプロセス中、.wim ファイルのキャプチャに使用されるターゲットの必要容量は、分割プロセスに対応できるように 8 GB より大きい必要があります。  
  
####  <a name="step-3-create-the-server-recovery-dvd"></a><a name="BKMK_Creating"></a>手順 3: サーバー回復 DVD の作成  
 工場から出荷された各サーバーには、サーバー回復 DVD が付属していなければなりません。 ADK ツール DVD には、DVD を作成するために必要なファイルが含まれます。  
  
###### <a name="to-create-the-server-recovery-dvd"></a>サーバー回復 DVD を作成するには  
  
1.  最終 ISO を保存するための場所として使用する作業フォルダーを作成します。  
  
2.  パートナー CD から、手順 1 で作成した作業フォルダーに、 **[Server Recovery]** フォルダーの内容をコピーします。  
  
3.  GenDiskXML.exe の実行時に作成された disk.xml ファイルを **[リセット]** フォルダーにコピーします。  
  
4.  **GenDiskXML.exe** の実行時に作成されたイメージ ファイルを **[リセット]** フォルダーにコピーします。 これらのイメージ ファイルは .wim ファイルと .swm ファイルで、ファイル数は異なる可能性があります。  
  
5.  フォルダーから GenDiskXML.exe を削除します。 このファイルは工場での作業にのみ使用され、顧客に出荷する DVD に含めるものではありません。  
  
####  <a name="step-4-customize-the-wizard"></a><a name="BKMK_Customizing"></a>手順 4: ウィザードをカスタマイズする  
 サーバー回復アプリケーションは、デバイスのイメージ、および特定のデバイスを回復モードで開始する方法を記述したテキストを使用して、カスタマイズする必要があります。 ファイルおよびフォルダーの復元ウィザードのこのページはハードウェア固有のため、サーバーを回復モードで開始する手順は異なります。  
  
> [!NOTE]
>  一覧表示されているファイル名は正確に一致する必要があります。  
  
1. ウィザードのページには、追加のヘルプ用のリンクがあります。 この .chm ファイルが存在している場合、Web ヘルプ用の FWLink が上書きされます。 このヘルプ ファイルは次の場所にあります。  
  
    < DVD ルート\>\\$OEM $ \ カスタマイズ\\< カルチャ名\>\RestartHelp.chm  
  
2. このファイルには、ウィザード ページで顧客に表示されるテキストが含まれています。 このテキストでは、サーバーを回復モードで起動する方法について説明する必要があります。 コントロールはスクロール可能です。追加可能なテキストの量の制限は、実質的な制限です。  
  
    次のファイルは、ウィザード内のサンプル画像を置き換えるために使用され、主にブランド化に関連します。 このファイルは .png ファイルである必要があります。 ファイル サイズは 256 ピクセル x 256 ピクセルである必要があります。このサイズより大きい場合、ウィザードで表示される際にトリミングされます。  
  
    < DVD ルート\>\\$OEM $ \ カスタマイズ\\< カルチャ名\>\RestartInstructions.rtf  
  
3. < DVD ルート\>\\$OEM $ \ カスタマイズ\\< カルチャ名\>\ serverimage。  
  
   複数の言語をサポートするためにサーバー回復 DVD を変換する際には、必ず次の事項を実行してください。  
  
4. en-us フォルダーを作成しておく必要があります。 サーバー回復アプリケーションは、アプリケーションが実行されているクライアント コンピューターに一致するカルチャ固有のファイルを見つけられない場合、en-us にフォールバックします。  
  
5. 作成する各カルチャ フォルダーで、3 つのカスタマイズ ファイル (.png、.chm、rtf) を追加します。  
  
6. 言語パック\\< 選別 Turename\>\ server Recovery から、サーバー回復 DVD のルートに両方のカルチャフォルダーをコピーします。 たとえば、スペイン語をサポートするためには ES および ES-ES フォルダーの両方を DVD のルートにコピーします。  
  
7. ISO ファイルの最終処理を実行します。  
  
   サポートされているカルチャ名には次のようなものがあります。  

|-|-|  
|-cs-CS-CZ<br /><br /> -de<br /><br /> -en-us<br /><br /> -es<br /><br /> -fr-fr<br /><br /> -hu-HU<br /><br /> -it<br /><br /> -ja-jp<br /><br /> -ko-韓国<br /><br /> -nl-NL |-pl-PL<br /><br /> -pt-BR<br /><br /> -pt-PT<br /><br /> -ru-RU<br /><br /> -sv-SE<br /><br /> -tr-TR<br /><br /> -zh-tw-CN<br /><br /> -zh-tw-HK<br /><br /> -zh-tw-TW
  
####  <a name="step-5-create-the-iso-file"></a><a name="BKMK_CreatingISO"></a>手順 5: ISO ファイルを作成する  
 作成したフォルダーとすべての内容は、DVD に書き込むことができます。 これが新しいサーバーと共に顧客に提供される DVD となります。  
  
####  <a name="step-6-test-the-recovery-dvd"></a><a name="BKMK_Testing"></a>手順 6: 回復 DVD のテスト  
 サーバーのインストールが完了したら、サーバーのバックアップを構成および実行し、次に回復 DVD をテストします。  
  
###### <a name="to-configure-and-run-a-server-backup"></a>サーバーのバックアップを構成および実行するには  
  
1.  ダッシュボードを開き、 **[デバイス]** タブをクリックし、 **[タスク]** ウィンドウの **[サーバーのバックアップのセットアップ]** をクリックします。  
  
2.  ウィザードの指示に従って、バックアップ サーバーのバックアップを構成します。 バックアップ用に外部ハード ディスクが必要になります。  
  
3.  **[タスク]** ウィンドウの **[サーバーのバックアップの開始]** をクリックし、ウィザードの指示に従います。  
  
4.  バックアップが終了したら、成功したことを確認します。  
  
###### <a name="to-restore-a-server"></a>サーバーを復元するには  
  
1.  作成した回復 DVD を、ハブまたはスイッチ経由でサーバーと同じネットワークに接続されているクライアント コンピューターに挿入します。  
  
2.  **setup.exe** をダブルクリックします。 サーバー回復ウィザードによって、顧客が実行するプロセスと同じプロセスを実行するよう要求されます。  
  
3.  **[サーバーをバックアップから復元する]** をクリックし、ウィザードの指示に従います。  
  
## <a name="see-also"></a>参照  
 [イメージ  の作成とカスタマイズ](Creating-and-Customizing-the-Image.md)  
 [追加のカスタマイズ](Additional-Customizations.md)   
 [展開  のイメージの準備](Preparing-the-Image-for-Deployment.md)  
 [カスタマー エクスペリエンスのテスト](Testing-the-Customer-Experience.md)