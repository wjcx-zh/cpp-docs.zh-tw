---
title: "編譯器錯誤 C2355 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 76d274ee94c20502a0ca6f167a9fce1f1dbf9465
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2355"></a>編譯器錯誤 C2355
'this'：只能在非靜態成員函式或非靜態資料成員初始設定式內部參考  
  
 `this` 指標只在非靜態成員函式或非靜態資料成員初始設定式內部才有效。 在類別宣告之外的成員函式定義的類別範圍不正確地限定時，就會產生這個錯誤。 在該類別中未宣告的函式中使用 `this` 指標時，也可能會發生錯誤。  
  
 若要修正此問題，請確定成員函式定義符合類別中的成員函式宣告，而且未宣告為靜態。 關於資料成員初始設定式，請確定資料成員未宣告為靜態。  
  
 下列範例會產生 C2355，並示範如何修正此問題：  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```
