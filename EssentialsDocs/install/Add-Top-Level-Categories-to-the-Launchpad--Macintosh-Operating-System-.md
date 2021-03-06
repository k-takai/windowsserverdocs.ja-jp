---
title: 最上位のカテゴリをスタートパッドに追加する (Macintosh オペレーティング システム)
description: Windows Server Essentials の使用方法について説明します。
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee2173c3-e464-4001-9f43-6d926a575092
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 3b16cadc14999e041dc6b1661689787e434460eb
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80310221"
---
# <a name="add-top-level-categories-to-the-launchpad-macintosh-operating-system"></a>最上位のカテゴリをスタートパッドに追加する (Macintosh オペレーティング システム)

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Macintosh オペレーティン グシステムを実行しているコンピューター上のスタート パッドに最上位のカテゴリを追加できます。 最上位のカテゴリを追加するスタートパッドアドインを作成するには、このページの情報と、「方法: タスクとカテゴリをスタートパッドに追加する」のトピックの情報を組み合わせて使用します。[Windows Server SOLUTIONS SDK](https://go.microsoft.com/fwlink/?LinkID=248648)。  
  
 次の例は、.launchpad ファイルで最上位のカテゴリにするスタートパッド エントリを指定する方法を示します。  
  
```  
  
<?xml version="1.0" encoding="utf-8" ?>  
<LaunchPad resFile="Localizable">  
   <Category id="Microsoft.Launchpad.HomeCategory" name="SampleAddin"  image="SampleImage01.png">  
      <Task id="Microsoft.Launchpad.SampleAddin.Pictures"   
          name="Pictures"       
           src="smb://%ServerAddress%/Pictures"   
         image="SampleImage02.png"/>  
   </Category>  
</LaunchPad>  
```  
  
 エントリを最上位のカテゴリにするには、カテゴリ要素の Id 属性が "Microsoft.Launchpad.HomeCategory" でなければなりません。  
  
## <a name="see-also"></a>参照  
 [イメージ  の作成とカスタマイズ](Creating-and-Customizing-the-Image.md)  
 [追加のカスタマイズ](Additional-Customizations.md)   
 [展開  のイメージの準備](Preparing-the-Image-for-Deployment.md)  
 [カスタマー エクスペリエンスのテスト](Testing-the-Customer-Experience.md)