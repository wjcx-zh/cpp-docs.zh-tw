---
title: 編譯器警告 C4484 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75531c207f0136f16109b4d69d689b883998aae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4484"></a>編譯器警告 C4484
'override_function': 符合基底 ref 類別方法 'base_class_function'，但未標記為 'virtual'、 ' new' override';'new' （而非 'virtual'） 會假設  
  
 編譯時 **/clr**，編譯器不會隱含地覆寫基底類別函式，這表示函式會取得在 vtable 中的新位置。 若要解決，請明確指定函式是否覆寫。  
  
 如需詳細資訊，請參閱:  
  
-   [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [new （新位置 vtable 中）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484 永遠視為錯誤。 使用[警告](../../preprocessor/warning.md)隱藏 C4484 pragma。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4484。  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```