---
title: 編譯器警告 （層級 1） C4488 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3c5fc64637d989066acfa90715c50504664231
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4488"></a>編譯器警告 (層級 1) C4488
'function': 需要 'keyword' 關鍵字來實作介面方法 'interface_method'  
  
 類別必須實作所有介面直接繼承的成員。 實作的成員必須具有公用存取範圍，並必須標記為 virtual。  
  
## <a name="example"></a>範例  
 如果實作的成員不是公用，則可能會發生 C4488。 下列範例會產生 C4488。  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## <a name="example"></a>範例  
 如果實作的成員未標記為 virtual，可能會發生 C4488。 下列範例會產生 C4488。  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```