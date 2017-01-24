---
title: "資源編譯器嚴重錯誤 RC1015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1015"
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器嚴重錯誤 RC1015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟 Include 檔 'filename'  
  
 給定的包含檔案不存在、無法開啟或是找不到。  
  
 請確定環境設定有效，且指定的檔案路徑正確。  請確認資源編譯器具有足夠的檔案控制代碼。  如果檔案位於網路磁碟機上，請先確認您是否具有開啟檔案的權限。  
  
 即使 Include 檔存在於 \[組態屬性\] \-\> \[資源\] \-\> \[一般\] 屬性頁的 \[其他 Include 目錄\] 目錄中，也可能發生 RC1015；請指定 Include 檔所在位置的完整路徑。  
  
 如需詳細資訊，請參閱知識庫 \(Knowledge Base\) 文件 Q326987「RC1015 Error When Using Resource View If the Include Path is Too Long」。