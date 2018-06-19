---
title: 編譯器錯誤 C2594 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1de853b8992d3c02eb94c0b050d72539fc3282
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230686"
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