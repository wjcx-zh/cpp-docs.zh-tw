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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdf6737c881df52793e1f59f04a1821a3c788134
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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