---
title: "編譯器錯誤 C2228 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2f16e67f67ac00fa17f6b60f70af53ae7345df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2228"></a>編譯器錯誤 C2228
'.identifier' 的左邊必須有類別/結構/等位  
  
 句號 （.） 左邊的運算元不是類別、 結構或等位。  
  
 下列範例會產生 C2228：  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 如果使用 Managed Extensions 時用了不正確的語法，您也會看到這個錯誤。 至於其他 Visual Studio 語言，您可以使用點運算子來存取 Managed 類別的成員，C++ 中的物件指標表示您必須使用 -> 運算子來存取成員：  
  
 錯誤： `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 正確： `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`