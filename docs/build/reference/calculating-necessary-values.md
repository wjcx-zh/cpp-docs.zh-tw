---
title: "計算需要的值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6351de62aa9141d98c5afabe1425d4586ca54371
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="calculating-necessary-values"></a>計算需要的值
計算方式是延遲 helper 常式需要兩項重要的資訊。 為了這個目的，有兩個內嵌函式 delayhlp.cpp 計算這項資訊。  
  
-   第一個計算目前匯入 （匯入位址表 (IAT)、 繫結的匯入位址資料表 (BIAT) 和未繫結的匯入位址資料表 (UIAT)） 的三個不同資料表的索引。  
  
-   第二個計算中有效的 IAT 的匯入的數目。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [了解協助協助程式函式](understanding-the-helper-function.md)