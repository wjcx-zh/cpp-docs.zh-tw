---
title: "計算需要的值 | Microsoft Docs"
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
  - "Helper 函式, 計算必要的值"
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 計算需要的值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有兩項必須由延遲 Helper 常式計算的關鍵資訊，  為此，delayhlp.cpp 中有兩個計算這項資訊的內嵌 \(Inline\) 函式。  
  
-   第一個函式會計算目前匯入三個不同表格 \(匯入位址表 \(IAT\)、繫結匯入位址表 \(BIAT\) 和未繫結匯入位址表 \(UIAT\)\) 的索引。  
  
-   第二個會函式計算有效 IAT 中的匯入數量。  
  
```  
// utility function for calculating the index of the current import  
// for all the tables (INT, BIAT, UIAT, and IAT).  
__inline unsigned  
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {  
    return pitdCur - pitdBase;  
    }  
  
// utility function for calculating the count of imports given the base  
// of the IAT. NB: this only works on a valid IAT!  
__inline unsigned  
CountOfImports(PCImgThunkData pitdBase) {  
    unsigned        cRet = 0;  
    PCImgThunkData  pitd = pitdBase;  
    while (pitd->u1.Function) {  
        pitd++;  
        cRet++;  
        }  
    return cRet;  
    }  
```  
  
## 請參閱  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-tw/6279c12c-d908-4967-b0b3-cabfc3e91d3d)