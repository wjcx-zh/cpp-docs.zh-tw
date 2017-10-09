---
title: "編譯器錯誤 C2015 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4669eec9d8134db6e024257855012eb78dcef95e
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2015"></a>編譯器錯誤 C2015
常數中有太多字元  
  
 字元常數中包含兩個以上的字元。 限制為標準字元常數的一個字元，請使用兩個字元長的字元常數。  
  
 逸出序列，例如 \t，會轉換成單一字元。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2015:  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## <a name="example"></a>範例  
 使用 Microsoft 擴充功能，轉換為整數字元常數時，也會發生 C2015。  下列範例會產生 C2015:  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```
