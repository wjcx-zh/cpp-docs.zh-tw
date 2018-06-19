---
title: 編譯器錯誤 C2391 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2391
dev_langs:
- C++
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a16ed19f5cac9d6c23a3f709e40fc290223e93c7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224761"
---
# <a name="compiler-error-c2391"></a>編譯器錯誤 C2391
'identifier': 'friend' 不能在類型定義  
  
 `friend`宣告包含完整的類別宣告。 A`friend`成員函式或複雜的類型規範，但不是完整的類別宣告，可以指定宣告。  
  
 下列範例會產生 C2326：  
  
```  
// C2391.cpp  
// compile with: /c  
class D {   
   void func( int );   
};  
  
class A {  
   friend class B { int i; };   // C2391  
  
   // OK  
   friend class C;  
   friend void D::func(int);  
};  
```