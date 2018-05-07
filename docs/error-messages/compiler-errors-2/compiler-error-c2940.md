---
title: 編譯器錯誤 C2940 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2940
dev_langs:
- C++
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17f9a89f4adb2da1ef10ae17301e0b36452e43fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2940"></a>編譯器錯誤 C2940
'class': type-class-id 重複定義為區域 typedef  
  
 您無法使用泛型或範本類別作為本機 `typedef`。  
  
 下列範例會產生 C2940：  
  
```  
// C2940.cpp  
template<class T>  
struct TC {};   
int main() {  
   typedef int TC<int>;   // C2940  
   typedef int TC;   // OK  
}  
```  
  
 使用泛型時，也會發生 C2940：  
  
```  
// C2940b.cpp  
// compile with: /clr  
generic<class T>  
ref struct GC { };  
  
int main() {  
   typedef int GC<int>;   // C2940  
   typedef int GC;  
}  
```