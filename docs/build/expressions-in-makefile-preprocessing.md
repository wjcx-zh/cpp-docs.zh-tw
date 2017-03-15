---
title: "Makefile 前置處理中的運算式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算式 [C++], Makefile 前置處理"
  - "Makefile, 前置處理"
  - "前置處理 Makefile"
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Makefile 前置處理中的運算式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\!IF** 或 **\!ELSE IF** `constantexpression` 是由整數常數 \(以十進位或 C 語言標記法表示\)、字串常數，或命令所組成。  使用括號群組運算式。  運算式使用 C\-Style 帶正負號的長整數運算，數字則是 32 位元的對 2 補數格式，範圍從 \-2147483648 至 2147483647 之間。  
  
 運算式可以使用在常數值、命令的結束代碼、字串、巨集，以及檔案系統路徑上執行的運算子。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [Makefile 前置處理運算子](../build/makefile-preprocessing-operators.md)  
  
 [在前置處理中執行程式](../build/executing-a-program-in-preprocessing.md)  
  
## 請參閱  
 [Makefile 前置處理](../build/makefile-preprocessing.md)