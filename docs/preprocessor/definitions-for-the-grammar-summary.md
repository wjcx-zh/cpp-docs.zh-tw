---
title: "文法摘要的定義 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "前置處理器"
  - "前置處理器, 定義"
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文法摘要的定義
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

終端是語法定義的端點。  沒有其他解決方式。  終端包括一組保留字和使用者定義的識別項。  
  
 非終端在語法中是預留位置。  大部分是在此語法摘要中的其他位置定義。  定義可以是遞迴式。  《C\+\+ 語言參考》的[文法摘要](../misc/grammar-summary-cpp.md)中定義了下列非終端：  
  
 `constant`、*constant\-expression*、*identifier*、*keyword*、`operator`、`punctuator`  
  
 選擇性的元件會以下標的 opt 表示。  例如，以下表示以大括號括住的選擇性運算式：  
  
 **{** *expression*opt **}**  
  
## 請參閱  
 [文法摘要](../preprocessor/grammar-summary-c-cpp.md)