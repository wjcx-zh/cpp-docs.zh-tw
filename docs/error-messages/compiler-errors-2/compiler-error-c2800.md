---
title: 編譯器錯誤 C2800 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd9723513042ae7ef6d63914f5abecd63192e37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235593"
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