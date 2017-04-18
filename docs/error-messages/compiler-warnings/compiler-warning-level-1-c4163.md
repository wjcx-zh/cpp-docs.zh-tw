---
title: "編譯器警告 （層級 1） C4163 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4163
dev_langs:
- C++
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 53538ee7959112e1a2cb04a727fda54d7afb995e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4163"></a>編譯器警告 (層級 1) C4163
'identifier' : 無法當做內建函式使用  
  
 指定的函式不能當做[內建](../../preprocessor/intrinsic.md)函式。 編譯器會忽略無效的函式名稱。  
  
 下列範例會產生 C4163：  
  
```  
// C4163.cpp  
// compile with: /W1 /LD  
#include <math.h>  
#pragma intrinsic(mysin)   // C4163  
// try the following line instead  
// #pragma intrinsic(sin)  
```
