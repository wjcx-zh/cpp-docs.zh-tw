---
title: "編譯器錯誤 C2070 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0923caf84c3980c4ee1b4eaa832752f34a447cc1
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2070"></a>編譯器錯誤 C2070
'type': 不合法的 sizeof 的運算元  
  
 [Sizeof](../../cpp/sizeof-operator.md)運算子需要運算式或類型的名稱。  
  
 下列範例會產生 C2070:  
  
```  
// C2070.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(func);   // C2070  
}  
```  
  
 可能的解決方式：  
  
```  
// C2070b.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(a);  
}  
```
