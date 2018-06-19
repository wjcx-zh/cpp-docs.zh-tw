---
title: 編譯器錯誤 C2802 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2802
dev_langs:
- C++
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe069b93c8dc6bb098927925e93f10cec2dbc4c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236653"
---
# <a name="compiler-error-c2802"></a>編譯器錯誤 C2802
靜態成員 'operator operator' 具有沒有型式參數  
  
 由運算子宣告`static`成員函式必須有至少一個參數。  
  
 下列範例會產生 C2802:  
  
```  
// C2802.cpp  
// compile with: /clr /c  
ref class A {  
   static operator+ ();   // C2802  
   static operator+ (A^, A^);   // OK  
};  
```