---
title: 編譯器錯誤 C2665 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18cc99d6ea0a45e7c096a13cfe57dc841ca351bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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