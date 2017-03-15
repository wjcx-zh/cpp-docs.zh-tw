---
title: "編譯器警告 (層級 1) C4124 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4124"
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_fastcall 與堆疊檢查並用會降低執行效能  
  
 `__fastcall` 關鍵字與已啟用的堆疊檢查一起使用。  
  
 `__fastcall` 慣例會產生較快的程式碼，但堆疊檢查會導致程式碼速度變慢。  使用 `__fastcall` 時，請使用 **check\_stack** pragma 或 \/Gs 關閉堆疊檢查。  
  
 這個警告只會在這些條件下宣告第一個函式時發出。