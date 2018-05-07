---
title: 編譯器錯誤 C2903 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2903
dev_langs:
- C++
helpviewer_keywords:
- C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c822870f9e73b28a5ebeb7fd43438054e45ee75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2903"></a>編譯器錯誤 C2903
'identifier': 符號不是類別樣板，也不是函式樣板  
  
 程式碼嘗試明確具現化非樣板的某個項目。  
  
 下列範例會產生 C2903：  
  
```  
// C2903.cpp  
// compile with: /c  
namespace N {  
   template<class T> class X {};  
   class Y {};  
}  
void g() {  
   N::template Y y;   // C2903  
   N::X<N::Y> y;   // OK  
}  
```  
  
 使用泛型時，也會發生 C2903：  
  
```  
// C2903b.cpp  
// compile with: /clr /c  
namespace N {  
   class Y {};  
   generic<class T> ref class Z {};  
}  
  
void f() {  
   N::generic Y y;   // C2903  
   N:: generic Z<int>^ z;   // OK  
}  
```