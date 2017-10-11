---
title: "編譯器錯誤 C2798 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bb0a411651cf7c7f614942563baee5f04075fdf3
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2798"></a>編譯器錯誤 C2798
'super::member' 模稜兩可  
  
 多重繼承的結構包含您使用參考成員[super](../../cpp/super.md)。 您無法透過其中一種來修正錯誤：  
  
-   D.的繼承清單中移除 B1 或 B2  
  
-   變更 B2 B1 中的資料成員的名稱。  
  
 下列範例會產生 C2798:  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```
