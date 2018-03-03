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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a04a5c113ca39dac137f2f225a8dcad9318a29bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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