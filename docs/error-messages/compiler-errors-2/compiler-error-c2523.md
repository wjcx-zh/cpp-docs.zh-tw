---
title: "編譯器錯誤 C2523 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d9ec6a9196498f210e680acf17efd34ac84faf77
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2523"></a>編譯器錯誤 C2523
' 類別:: ~ 識別項 ': 解構函式/完成項標記不相符  
  
 解構函式名稱必須是類別名稱加上波狀符號 (`~`)。 建構函式和解構函式會，只有具有相同的名稱與類別的成員。  
  
 下列範例會產生 C2523:  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```
