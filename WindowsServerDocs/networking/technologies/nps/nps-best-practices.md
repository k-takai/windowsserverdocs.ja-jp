---
title: ネットワーク ポリシー サーバーのベスト プラクティス
description: このトピックでは、Windows Server 2016 でネットワークポリシーサーバーを展開および管理するためのベストプラクティスについて説明します。
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 90e544bd-e826-4093-8c3b-6a6fc2dfd1d6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 278d813aa13ea42b7f597bdbe7eb210f68cee955
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316303"
---
# <a name="network-policy-server-best-practices"></a>ネットワーク ポリシー サーバーのベスト プラクティス

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、NPS\)\(ネットワークポリシーサーバーを展開および管理するためのベストプラクティスについて説明します。

以下のセクションでは、NPS の展開のさまざまな側面に関するベストプラクティスについて説明します。

## <a name="accounting"></a>アカウンティング

NPS のログ記録のベストプラクティスを次に示します。

NPS には、次の 2 種類のアカウンティング (またはログ記録) が用意されています。

- NPS のイベントログ。 イベント ログを使用してシステム イベント ログおよびセキュリティ イベントログ内の NPS イベントを記録できます。 このログは、主に接続試行の監査およびトラブルシューティングに使用されます。

- ユーザー認証およびアカウンティング要求をログに記録します。 ユーザー認証要求およびアカウンティング要求をテキスト形式またはデータベース形式でログ ファイルに記録できます。また、SQL Server 2000 データベースのストアド プロシージャに記録することもできます。 要求ログは、主に接続分析と課金の目的で使用されます。また、セキュリティ調査ツールとしても役立ち、攻撃者のアクティビティを追跡する方法を提供します。

NPS のログを最大限に活用するには、次の操作を行います。

- 認証レコードとアカウンティングレコードの両方に対して最初に\) のログ \(をオンにします。 この設定は、環境に合わせて適切となるように後で変更します。

- イベント ログがログの管理に十分な容量をもって構成されていることを確認します。

- すべてのログファイルを定期的にバックアップします。これらのファイルは、破損または削除されたときに再作成することはできません。

- 使用量を追跡し、使用分を課金する部門またはユーザーを簡単に特定する 2 種類の目的のために RADIUS クラス属性を使用します。 要求ごとにクラス属性が自動的に生成されますが、アクセス サーバーへの応答が失われた場合や要求が再送された場合に、記録が重複することがあります。 重複した記録はログから削除し、使用量を正確に追跡できるようにする必要があります。

- ネットワークアクセスサーバーと RADIUS プロキシサーバーが、nps がオンラインであることを確認するために、架空の接続要求メッセージを NPS に定期的に送信する場合は、 **ping ユーザー名**レジストリ設定を使用します。 この設定は、NPS がこれらの偽の接続要求を処理せずに自動的に拒否するように構成します。 さらに、NPS は、架空のユーザー名を含むトランザクションをログファイルに記録しないため、イベントログの解釈が容易になります。

- NAS の通知転送を無効にします。 ネットワークアクセスサーバー (Nas) から、NPS で構成されているリモート RADIUS サーバーグループのメンバーへの開始および停止メッセージの転送を無効にすることができます。 詳細については、「 [DISABLE NAS Notification フォワーディング](nps-disable-nas-notifications.md)」を参照してください。

詳細については、「[ネットワークポリシーサーバーアカウンティングの構成](nps-accounting-configure.md)」を参照してください。

- SQL Server のログ記録にフェールオーバーと冗長性を持たせるには、SQL Server が実行されている 2 台のコンピューターを別のサブネットに配置します。 **パブリケーションの作成ウィザード**を使用して、2つのサーバー間のデータベースのレプリケーションを設定 SQL Server ます。 詳細については、 [SQL Server 技術ドキュメント](https://msdn.microsoft.com/library/ms130214.aspx)と[SQL Server レプリケーション](https://msdn.microsoft.com/library/ms151198.aspx)を参照してください。

## <a name="authentication"></a>認証

次に、認証についてのヒント集を挙げます。

- 強力な認証を行うために、保護された拡張認証プロトコル \(PEAP\) や拡張認証\) \(プロトコルなどの証明書ベースの認証方法を使用します。 パスワードのみの認証方法は、さまざまな攻撃に対して脆弱であり、セキュリティで保護されていないため、使用しないでください。 セキュリティで保護されたワイヤレス認証の場合、NPS はサーバー証明書を使用してワイヤレスクライアントに対して id を証明し、ユーザーはユーザー名とパスワードで id を証明するため、PEAP\-MS\-CHAP v2 を使用することをお勧めします。  ワイヤレス展開での NPS の使用の詳細については、「[パスワードベースの 802.1 x 認証ワイヤレスアクセスの展開](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access)」を参照してください。
- NPSs でサーバー証明書を使用する必要がある PEAP や EAP などの強力な証明書ベースの認証方法を使用する場合は、Active Directory&reg; 証明書サービス \(AD CS\) を使用して、独自の証明機関 \(CA\) を展開します。 また、独自の CA を使用してコンピューター証明書およびユーザー証明書を登録できます。 NPS とリモートアクセスサーバーにサーバー証明書を展開する方法の詳細については、「 [802.1 x ワイヤードおよびワイヤレス展開用のサーバー証明書の展開](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments)」を参照してください。

> [!IMPORTANT]
> ネットワークポリシーサーバー (NPS) では、パスワード内の拡張 ASCII 文字の使用はサポートされていません。

## <a name="client-computer-configuration"></a>クライアント コンピューターの構成

次に、クライアント コンピューターの構成についてのヒント集を挙げます。

- グループポリシーを使用して、すべてのドメインメンバー 802.1 X クライアントコンピューターを自動的に構成します。 詳細については、「[ワイヤレスアクセスの展開](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/e-wireless-access-deployment#bkmk_policies)」の「ワイヤレスネットワーク (IEEE 802.11) ポリシーの構成」セクションを参照してください。

## <a name="installation-suggestions"></a>インストールに関する提案

次に、NPS をインストールするためのベストプラクティスを示します。

- NPS をインストールする前に、ローカル認証方法を使用して各ネットワークアクセスサーバーをインストールし、テストしてから、NPS で RADIUS クライアントとして構成します。

- NPS をインストールして構成した後、Windows PowerShell コマンド[Export-NpsConfiguration](https://technet.microsoft.com/library/jj872749.aspx)を使用して構成を保存します。 Nps を再構成するたびに、このコマンドを使用して NPS 構成を保存します。

>[!CAUTION]
>- エクスポートされた NPS 構成ファイルには、RADIUS クライアントおよびリモート RADIUS サーバーグループのメンバー用の暗号化されていない共有シークレットが含まれています。 このため、ファイルを安全な場所に保存してください。
>- エクスポートプロセスには、エクスポートされたファイルの Microsoft SQL Server のログ設定は含まれません。 エクスポートしたファイルを別の NPS にインポートする場合は、新しいサーバーで SQL Server ログを手動で構成する必要があります。

## <a name="performance-tuning-nps"></a>NPS のパフォーマンスチューニング

NPS のパフォーマンスチューニングのベストプラクティスを次に示します。

- NPS の認証および承認の応答時間を最適化し、ネットワーク トラフィックを最小化するには、NPS をドメイン コントローラー上にインストールします。

- ユニバーサルプリンシパル名 \(Upn\) または Windows Server 2008 および Windows Server 2003 ドメインが使用されている場合、NPS はグローバルカタログを使用してユーザーを認証します。 この処理にかかる時間を最小限に抑えるには、グローバルカタログサーバーまたはグローバルカタログサーバーと同じサブネット上にあるサーバーのどちらかに NPS をインストールします。

- リモート RADIUS サーバーグループが構成されていて、NPS 接続要求ポリシーで [**次のリモート radius サーバーグループのサーバーのアカウンティング情報を記録**する] チェックボックスをオフにした場合、これらのグループは引き続きネットワークアクセスサーバー \(NAS\) 開始および停止通知メッセージを送信します。 そのため、ネットワーク トラフィックが不必要に増大することになります。 このトラフィックを排除するには、 **[このサーバーへの通知を開始および停止する]** チェックボックスをオフにして、各リモート RADIUS サーバーグループ内の個々のサーバーの NAS 通知転送を無効にします。

## <a name="using-nps-in-large-organizations"></a>NPS を大規模な組織で使用する

大規模な組織で NPS を使用する場合のベストプラクティスを次に示します。

- ネットワークポリシーを使用して、特定のグループに限定してアクセスを制限する場合は、アクセスを許可するすべてのユーザーに対してユニバーサルグループを作成し、このユニバーサルグループにアクセス権を付与するネットワークポリシーを作成します。 アクセスを許可するユーザーがネットワーク上に多数いる場合は特に、すべてのユーザーを直接ユニバーサル グループに追加しないでください。 代わりに、ユニバーサル グループのメンバーとして個別にグループを作成し、これらのグループにユーザーを追加します。

- 可能な場合は常に、ユーザーの参照にはユーザー プリンシパル名を使用します。 ドメインのメンバーであるかどうかにかかわらず、ユーザーには同じユーザー プリンシパル名を付けることができます。 こうすることで、ドメインが多数ある組織に必要となる拡張性が実現します。

- ドメインコントローラー以外のコンピューターにネットワークポリシーサーバー \(NPS\) インストールし、NPS が1秒あたりに多数の認証要求を受信している場合は、nps とドメインコントローラー間で許可される同時認証の数を増やすことで、NPS のパフォーマンスを向上させることができます。 詳細については、 を参照してください。 

## <a name="security-issues"></a>セキュリティに関する問題

セキュリティの問題を軽減するためのベストプラクティスを次に示します。

NPS をリモートで管理している場合は、機密データ (共有シークレットやパスワードなど) をプレーンテキストでネットワーク経由で送信しないでください。 NPSs のリモート管理には、次の2つの方法をお勧めします。

- リモートデスクトップサービスを使用して NPS にアクセスします。 リモートデスクトップサービスを使用すると、クライアントとサーバーの間でデータが送信されません。 サーバーのユーザーインターフェイス (オペレーティングシステムデスクトップ、NPS コンソールイメージなど) のみがリモートデスクトップサービスクライアントに送信されます。このクライアントには、Windows&reg; 10 でリモートデスクトップ接続という名前が付けられています。 クライアントは、リモートデスクトップサービス有効になっているサーバーによってローカルで処理される、キーボード入力とマウス入力を送信します。 リモートデスクトップサービスユーザーがログオンすると、サーバーによって管理され、互いに独立している個々のクライアントセッションのみを表示できます。 さらに、リモート デスクトップ接続では、クライアントとサーバーとの間に 128 ビットの暗号化方式が使用されます。

- 機密情報の暗号化にインターネット プロトコル セキュリティ (IPsec) を使用する。 IPsec を使用すると、nps と nps の管理に使用しているリモートクライアントコンピューター間の通信を暗号化できます。 サーバーをリモートで管理するには、クライアントコンピューターに[Windows 10 用のリモートサーバー管理ツール](https://www.microsoft.com/download/details.aspx?id=45520)をインストールします。 インストール後、Microsoft 管理コンソール (MMC) を使用して、NPS スナップインをコンソールに追加します。

>[!IMPORTANT]
>Windows 10 Professional または Windows 10 Enterprise の完全リリースでのみ、Windows 10 のリモートサーバー管理ツールをインストールできます。

NPS の詳細については、「[ネットワークポリシーサーバー (nps)](nps-top.md)」を参照してください。

