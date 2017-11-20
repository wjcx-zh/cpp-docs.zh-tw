---
title: "編譯器錯誤 C2193 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2193
dev_langs: C++
helpviewer_keywords: C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e59b7e3ab659ee7760254680e51db9e2d4ca35d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2193"></a>編譯器錯誤 C2193
'identifier': 已經在區段  
  
 函式已放在兩個不同的區段使用`alloc_text`和`code_seg`pragma。  
  
 下列範例會產生 C2193:  
  
```  
// C2193.cpp  
// compile with: /c  
extern "C" void MYFUNCTION();  
#pragma alloc_text(MYCODE, MYFUNCTION)  
#pragma code_seg("MYCODE2")  
extern "C" void MYFUNCTION() {}   // C2193  
extern "C" void MYFUNCTION2() {}  
```