---
title: "編譯器錯誤 C2652 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2652
dev_langs: C++
helpviewer_keywords: C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56cfdf52ec3a6947a6a82774f551fc1a6880c959
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2652"></a>編譯器錯誤 C2652
'identifier': 不合法的複製建構函式： 第一個參數不得為 'identifier'  
  
 複製建構函式的第一個參數具有相同的類別、 結構或等位為其定義的型別。 第一個參數可以是參考的類型，但不是類型本身。  
  
 下列範例會產生 C2651:  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```