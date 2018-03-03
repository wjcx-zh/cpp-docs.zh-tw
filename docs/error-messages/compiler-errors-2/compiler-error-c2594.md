---
title: "編譯器錯誤 C2594 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4cca18672aad77e051ff4428dc115c53cd5ddad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2594"></a>編譯器錯誤 C2594
'operator': 從 'type1' 模稜兩可的轉換成 'type2'  
  
 沒有從轉換*type1*至*type2*比其他更直接的。 我們建議兩種可能的解決方案從轉換*type1*至*type2*。 第一個選項是定義從直接轉換*type1*至*type2*，且第二個選項來指定從轉換的序列*type1*至*type2*。  
  
 下列範例會產生 C2594。 錯誤的建議解決方法是一串轉換：  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```