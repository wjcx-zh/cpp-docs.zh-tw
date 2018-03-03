---
title: "編譯器警告 （層級 4） C4481 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4481
dev_langs:
- C++
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52c296251e22adef2702aa9feba2b1fe2bc5122e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4481"></a>編譯器警告 (層級 4) C4481
使用非標準擴充： 覆寫規範 'keyword'  
  
 使用不在 c + + 標準，例如，有一個也能在 /clr 下運作的覆寫規範的關鍵字。  如需詳細資訊，請參閱：  
  
-   [/clr （common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>範例  
 下列範例會產生 C4481。  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```