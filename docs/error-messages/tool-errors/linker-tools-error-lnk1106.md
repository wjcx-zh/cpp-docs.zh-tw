---
title: "連結器工具錯誤 LNK1106 | Microsoft Docs"
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
  - "LNK1106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1106"
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1106
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案無效或磁碟已滿: 無法搜尋到 location  
  
 工具無法讀取或寫入至記憶體映射檔中的 `location`。  
  
### 若要修正，請檢查下列可能原因  
  
1.  磁碟已滿。  
  
     釋放部分空間並重新連結。  
  
2.  嘗試透過網路連結。  
  
     某些網路無法完全支援此連結器所使用的記憶體映射檔。  請嘗試在本機磁碟上進行連結。  
  
3.  磁碟有錯誤區塊。  
  
     雖然作業系統和磁碟硬體應該會偵測出這種錯誤，我們仍然建議您執行磁碟檢查程式。  
  
4.  堆積空間不足。  
  
     如需詳細資訊，請參閱 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)。