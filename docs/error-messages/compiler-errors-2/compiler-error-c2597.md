---
title: "編譯器錯誤 C2597 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d110b67adda70ef47cfd9b06addd4370e22c5788
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2597"></a>編譯器錯誤 C2597
參考非靜態成員 'identifier' 是不合法的  
  
 可能的原因：  
  
1.  非靜態成員是在靜態成員函式中指定。 若要存取非靜態成員，您必須傳入或建立類別的本機執行個體，並使用成員存取運算子 (`.` 或 `->`)。  
  
2.  指定的識別項不是類別、結構或等位的成員。 請檢查識別項拼寫。  
  
3.  成員存取運算子是指非成員函式。  
  
4.  下列範例會產生 C2597，並示範如何修正此問題：  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
```
