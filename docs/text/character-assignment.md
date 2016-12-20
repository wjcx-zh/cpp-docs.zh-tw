---
title: "字元設定 | Microsoft Docs"
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
  - "字元 [C++], 設定"
  - "MBCS [C++], 字元設定"
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 字元設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

考慮下列範例，其中 `while` 迴圈掃瞄一字串，將除了 "X" 之外的所有字元複製到另一個字串：  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 程式碼複製 `sz2` 的位元組到 `sz1` 所指的位置，然後增量 `sz1` 以接收下一個位元組。  但是如果 `sz2` 內的下一個字元是雙位元組字元，`sz1` 的指派會只複製第一個位元組。  下列程式碼使用可移植的函式來安全的複製字元，並使用另一個函示來正確的增量 `sz1` 和 `sz2`：  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [字元比較](../text/character-comparison.md)