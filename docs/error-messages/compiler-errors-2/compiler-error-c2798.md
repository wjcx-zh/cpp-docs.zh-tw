---
title: 編譯器錯誤 C2798 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de30a19a2a27cde991cfce0ca061ce6f5447f033
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236903"
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