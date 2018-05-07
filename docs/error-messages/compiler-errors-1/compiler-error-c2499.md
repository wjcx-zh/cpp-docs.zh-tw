---
title: 編譯器錯誤 C2499 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2499
dev_langs:
- C++
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6933d27a1f396dc08275c3f5149212be7abeaaf1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2499"></a>編譯器錯誤 C2499
'class': 類別不能自己的基底類別  
  
 您嘗試將指定基底類別中定義的類別。  
  
 下列範例會產生 C2499:  
  
```  
// C2499.cpp  
// compile with: /c  
class CMyClass : public CMyClass {};   // C2499  
class CMyClass{};   // OK  
```