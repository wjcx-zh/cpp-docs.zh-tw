---
title: "增量和遞減指標 | Microsoft Docs"
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
  - "遞減指標"
  - "遞增指標"
  - "MBCS [C++], 指標"
  - "指標 [C++], 多位元組字元"
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 增量和遞減指標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   指向前導位元組，而非後隨位元組。  讓指標指向後隨位元組通常是不安全的。  向前掃描字串通常會比反過來掃描還安全。  
  
-   在整個字元上移動時，可以使用的指標增量\/遞減函式和巨集：  
  
    ```  
    sz1++;  
    ```  
  
     變成：  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` 和 `_mbsdec` 函式正確的以 `character` 單位來增量和遞減，不管字元的大小。  
  
-   要遞減，您需要指向字串標頭的指標，如同下列所示：  
  
    ```  
    sz2--;  
    ```  
  
     變成：  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     另一種方法是，您的「標頭」指標可以指向字串中有效的字元，如此一來：  
  
    ```  
    sz2Head < sz2  
    ```  
  
     您必須有指向已知有效的前導位元組的指標。  
  
-   您可能想要保留指向前一個字元的指標，以提供對 `_mbsdec` 的快速呼叫。  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [位元組索引](../text/byte-indices.md)