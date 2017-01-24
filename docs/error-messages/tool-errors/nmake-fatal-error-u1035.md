---
title: "NMAKE 嚴重錯誤 U1035 | Microsoft Docs"
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
  - "U1035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1035"
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 必須是 ':' 或 '\=' 分隔符號  
  
 應該有冒號 \(**:**\) 或等號 \(**\=**\)。  
  
### 若要修正，請檢查下列可能原因  
  
1.  冒號沒有接在目標之後。  
  
2.  單一字母目標後跟隨著冒號，當中沒有空格 \(例如 a:\)。  NMAKE 將它解譯為磁碟機代號。  
  
3.  冒號沒有接在推斷規則 \(Inference Rule\) 之後。  
  
4.  巨集定義後沒有跟隨著等號。  
  
5.  有字元接在用於將命令延續至新行的反斜線 \(**\\**\) 之後。  
  
6.  出現不符合 NMAKE 語法規則的字串。  
  
7.  Makefile 由文書處理器格式化。