---
title: "編譯器錯誤 C2533 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c023fb47b0e2653cd7bf13b188b907558573a0ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2533"></a>編譯器錯誤 C2533
'identifier'：建構函式不允許傳回型別  
  
 建構函式不能有傳回類型 (甚至是 `void` 傳回類型也不可以)。  
  
 此錯誤的常見來源是類別定義結尾與第一個建構函式實作之間遺漏分號。 編譯器會將類別視為建構函式的傳回類型定義，並產生 C2533。  
  
 下列範例會產生 C2533，並示範如何修正此問題：  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```