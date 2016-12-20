---
title: "C 執行階段錯誤 R6002 | Microsoft Docs"
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
  - "R6002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6002"
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
caps.latest.revision: 10
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 執行階段錯誤 R6002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未載入浮點支援  
  
 沒有連結所需的浮點程式庫。  
  
### 若要修正，請檢查下列可能原因  
  
1.  程式以必須要有副處理器的選項 \(例如 \/FPi87\) 進行編譯或連結，但是執行程式的電腦上並沒有安裝副處理器。  
  
2.  `printf_s` 或 `scanf_s` 函式的格式字串 \(Format String\) 中包含浮點格式規格，但是該程式並沒有包含任何浮點數值或變數。  
  
3.  編譯器 \(Compiler\) 藉由只在必要時才載入浮點支援的方式，將程式的大小最小化。  但是編譯器無法偵測格式字串中的浮點規格，以致無法載入必須的浮點常式。  
  
4.  使用符合浮點格式規格的浮點引數，或是在程式的其他地方執行浮點指派。  這樣便可載入浮點支援。  
  
5.  在混合語言的程式中，程式連結時 C 程式庫在 FORTRAN 程式庫之前先指定。  重新連結並且最後指定 C 程式庫。