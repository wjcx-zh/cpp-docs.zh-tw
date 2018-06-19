---
title: 編譯器錯誤 C2015 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91c682aadeab5a572ec2bb5c2e649a1511af77ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165619"
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