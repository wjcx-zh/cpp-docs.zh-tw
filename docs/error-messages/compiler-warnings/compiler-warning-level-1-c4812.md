---
title: "編譯器警告 （層級 1） C4812 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4812
dev_langs:
- C++
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a52ef0b5af82481fae720b940ddbd35b2793fd55
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4812"></a>編譯器警告 (層級 1) C4812
過時的宣告樣式：請用 'new_syntax' 代替  
  
 在目前的 Visual C++ 版本中，仍然支援明確建構函式特製化，但未來的版本可能不予支援。  
  
 下列範例會產生 C4812：  
  
```  
// C4812.cpp  
// compile with: /W1 /c  
template <class T>   
class MyClass;  
  
template<class T>  
class MyClass<T*> {  
   MyClass();  
};  
  
template<class T>  
MyClass<T*>::MyClass<T*>() {}   // C4812  
// try the following line instead  
// MyClass<T*>::MyClass() {}  
```
