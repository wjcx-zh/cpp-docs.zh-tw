---
title: "嚴重錯誤 C1054 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1054"
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：初始設定式巢狀結構太深  
  
 程式碼超過了初始設定式的巢狀限制 \(10\-15 層，這將視初始化的型別組合而有所不同\)。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  簡化初始化的資料型別，以減少巢狀結構。  
  
2.  在宣告之後，初始化個別陳述式的變數