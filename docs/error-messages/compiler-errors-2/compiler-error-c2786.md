---
title: 編譯器錯誤 C2786 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2786
dev_langs:
- C++
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29fd0d8cf22be29757abd775e1bb844cb1a1bfbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232316"
---
# <a name="compiler-error-c2786"></a>編譯器錯誤 C2786
'type': __uuidof 的運算元無效  
  
 [__Uuidof](../../cpp/uuidof-operator.md)運算子採用的使用者定義型別與附加的 GUID 或這類使用者定義型別的物件。  可能的原因：  
  
1.  引數不是使用者定義型別。  
  
2.  `__uuidof` 無法擷取從引數的 GUID。  
  
 下列範例會產生 C2786:  
  
```  
// C2786.cpp  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
  
int main() {  
   __uuidof(int);   // C2786  
   __uuidof(int *);   // C2786  
   __uuidof(A **);   // C2786  
  
   // no error  
   __uuidof(A);  
   __uuidof(A *);  
   __uuidof(A &);  
   __uuidof(A[]);  
  
   int i;  
   int *pi;  
   A **ppa;  
  
   __uuidof(i);      // C2786  
   __uuidof(pi);     // C2786  
   __uuidof(ppa);    // C2786  
}  
```