---
title: "編譯器警告 C4485 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4485
dev_langs: C++
helpviewer_keywords: C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 435e49a857e3c448ac7e5f7ef00bb9032320aa25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4485"></a>編譯器警告 C4485
'override_function': 符合基底 ref 類別方法 'base_class_function'，但不是標示為 'new' override';'new' （和 'virtual'） 會假設  
  
 存取子會覆寫，不論`virtual`關鍵字、 基底類別存取子函式，但`override`或`new`規範不是覆寫的函式簽章的一部分。 新增`new`或`override`規範，以解決這個警告。  
  
 請參閱[覆寫](../../windows/override-cpp-component-extensions.md)和[新 (新 vtable 中的位置）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)如需詳細資訊。  
  
 C4485 永遠視為錯誤。 使用[警告](../../preprocessor/warning.md)隱藏 C4485 pragma。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```