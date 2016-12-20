---
title: "位元組索引 | Microsoft Docs"
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
  - "位元組索引 [C++]"
  - "MBCS [C++], 位元組索引"
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 位元組索引
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   對字串使用位元組類索引，會出現與指標管理所造成類似的問題。  考慮這個範例，掃瞄字串以尋找反斜線字元：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     這可能會索引後隨位元組 \(Trail Byte\)，而不是前導位元組 \(Lead Byte\)，所以可能不是指向 `character`。  
  
-   使用 [\_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) 函式來解決上述問題：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     這正確索引前導位元組，因此是指向 `character`。  `_mbclen` 函式決定字元的大小 \(1 個或 2 個位元組\)。  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [字串中的最後一個字元](../text/last-character-in-a-string.md)