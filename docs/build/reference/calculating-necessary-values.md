---
title: 計算需要的值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8f51e448aab0978d6a7eb39a753c2274d2cae6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369324"
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