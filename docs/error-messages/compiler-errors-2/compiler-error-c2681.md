---
title: "編譯器錯誤 C2681 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2681
dev_langs:
- C++
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9978a520b4682e4e2c7c4856d4e42675be0ab901
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2681"></a>編譯器錯誤 C2681
'type': 無效的運算式型別名稱  
  
 轉型運算子會嘗試將無效的型別轉換。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子，將運算式轉換成指標類型，來源運算式必須是指標。  
  
 下列範例會產生 C2681:  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```
