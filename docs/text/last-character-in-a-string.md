---
title: "字串中的最後一個字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字串中的最後一個字元"
  - "MBCS [C++], 字串中的最後一個字元"
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# 字串中的最後一個字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   後隨位元組在許多情況裡都與 ASCII 字元集重疊範圍。  您可以安全的使用位元組類掃瞄來尋找任何的控制字元 \(小於 32\)。  
  
-   考慮下列這行程式碼，它可能會檢查看字串裡的最後一個字元是不是反斜線字元：  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     因為 `strlen` 不是 MBCS 感知 \(MBCS\-aware\)，在多位元組字串裡，它會傳回位元組數目，而不是字元數目。  同時，請注意在一些字碼頁裡 \(例如，932\)，'\\' \(0x5c\) 是有效的後隨位元組 \(`sz` 是 C 字串\)。  
  
     一個可行的解決方法是以這種方式重寫程式碼：  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     這行程式碼使用 MBCS 函式 `_mbsrchr` 和 `_mbsinc`。  因為這些函式是 MBCS 感知，可以分辨 '\\' 字元和 '\\' 後隨位元組。  如果字串裡的最後一個字元是 Null \('\\0'\)，程式碼會執行某種動作。  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [字元設定](../text/character-assignment.md)