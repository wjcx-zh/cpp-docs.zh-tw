---
title: 編譯器錯誤 C2523 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4546e576ced8d57a35c4c4861f29824a8d91d910
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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