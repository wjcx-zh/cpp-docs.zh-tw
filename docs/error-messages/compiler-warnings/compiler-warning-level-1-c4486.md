---
title: 編譯器警告 （層級 1） C4486 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4486
dev_langs:
- C++
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91ad3659660dbe17552dc46caa66afe274ace9cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4486"></a>編譯器警告 (層級 1) C4486
'function': ref 類別或實值類別的私用虛擬方法標記為 'sealed'  
  
 因為無法存取或覆寫的受管理的類別或結構的私用虛擬成員函式，它應該標示[密封](../../windows/sealed-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4486。  
  
```  
// C4486.cpp  
// compile with: /clr /c /W1  
ref class B {  
private:  
   virtual void f() {}   // C4486  
   virtual void f1() sealed {}   // OK  
};  
```  
  
## <a name="example"></a>範例  
 下列範例會示範一個可能的私用密封虛擬函式的使用。  
  
```  
// C4486_b.cpp  
// compile with: /clr /c  
ref class B {};  
  
ref class D : B {};  
  
interface class I {  
   B^ mf();  
};  
  
ref class E : I {  
private:  
   virtual B^ g() sealed = I::mf {  
      return gcnew B;  
   }  
  
public:  
   virtual D^ mf() {  
      return gcnew D;  
   }  
};  
```