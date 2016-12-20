---
title: "C 執行階段錯誤 R6009 | Microsoft Docs"
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
  - "R6009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6009"
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 執行階段錯誤 R6009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

環境空間不足  
  
 有足夠的記憶體可以載入程式，但是沒有足夠的記憶體可以建立 **envp** 陣列。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  增加程式可使用的記憶體空間。  
  
2.  減少命令列引數的數目和大小。  
  
3.  藉由移除不需要的變數來減少環境大小。