---
title: "字元比較 | Microsoft Docs"
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
  - "字元 [C++], 比較"
  - "比較字元"
  - "MBCS [C++], 字元比較"
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# 字元比較
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   已知的前導位元組與 ASCII 字元之比較正常運作：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比較兩個未知字元需要使用 MBSTRING.H 所定義的巨集之一：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     這確保雙位元組字元的兩個位元組是作相等比較。  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [緩衝區溢位](../text/buffer-overflow.md)