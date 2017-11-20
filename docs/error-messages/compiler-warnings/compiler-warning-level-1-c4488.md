---
title: "編譯器警告 （層級 1） C4488 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4488
dev_langs: C++
helpviewer_keywords: C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1312d279eb9174e0863cae413a0014cc58710131
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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