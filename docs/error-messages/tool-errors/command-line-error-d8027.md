---
title: "命令列錯誤 D8027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8027"
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令列錯誤 D8027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法執行 'component'  
  
 編譯器無法執行給定的編譯器元件或連結器。  
  
### 若要修正，請檢查下列可能原因  
  
1.  沒有足夠的記憶體來載入元件。  如果是 NMAKE 叫用 \(Invoke\) 編譯器，請在 Makefile 之外執行編譯器。  
  
2.  目前的作業系統無法執行元件。  請確認路徑已指向適用於您作業系統的可執行檔案。  
  
3.  元件已損毀。  請使用安裝程式從安裝磁片上重新複製元件。  
  
4.  指定的選項不正確，  例如：  
  
    ```  
    cl /B1 file1.c  
    ```