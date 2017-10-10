---
title: "編譯器錯誤 C2750 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2750
dev_langs:
- C++
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: fbe3ee423183bb841e3e6777db94e4645b94355d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2750"></a>編譯器錯誤 C2750
'type': 參考類型; 無法使用 'new'請用 'gcnew' 代替  
  
 若要建立執行個體的 CLR 型別，這會導致要放在記憶體回收堆積上的執行個體，您必須使用[gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
 下列範例會產生 C2750:  
  
```  
// C2750.cpp  
// compile with: /clr  
ref struct Y1 {};  
  
int main() {  
   Y1 ^ x = new Y1;   // C2750  
  
   // try the following line instead  
   Y1 ^ x2 = gcnew Y1;  
}  
```
