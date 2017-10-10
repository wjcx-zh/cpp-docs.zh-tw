---
title: "編譯器錯誤 C2800 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 330b859b4b24f741388be716fb464fc33c3abaa3
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2800"></a>編譯器錯誤 C2800
不能多載 'operator operator'  
  
 下列的運算子無法多載： 類別成員存取 (`.`)、 成員指標 (`.*`)，範圍解析 (`::`)，條件運算式 (`? :`)，和`sizeof`。  
  
 下列範例會產生 C2800:  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```
