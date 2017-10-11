---
title: "編譯器錯誤 C2665 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5a349df2c60d746b6b090953362c7c6801e1f2a3
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2665"></a>編譯器錯誤 C2665
'function': 沒有任何數字 1 多載可以轉換參數 number2 從類型 'type'  
  
 多載函式的參數無法轉換為要求的類型。  可能的解決方式：  
  
-   提供轉換運算子。  
  
-   使用明確轉換。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2665。  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```
