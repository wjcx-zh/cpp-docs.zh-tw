---
title: "編譯器警告 （層級 1） C4533 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4533
dev_langs: C++
helpviewer_keywords: C4533
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 729e069612a72799a37135298f9ccce6c36e8a7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4533"></a>編譯器警告 (層級 1) C4533
'variable' 的初始化會被 '指令' 略過  
  
 指令程式中的變更控制項的流量，使得初始化變數的指令，所以未執行。 下列範例會產生 C4533:  
  
```  
// C4533.cpp  
// compile with: /W1  
#include <stdio.h>  
  
struct A  
{  
   int m_data;  
};  
  
int main()  
{  
   if (1)  
   {  
      goto Label;  
   }  
  
   A a = { 100 };  
  
   Label:   // C4533  
      printf("\n%d", a.m_data);   // prints an uninitialized value  
}  
```