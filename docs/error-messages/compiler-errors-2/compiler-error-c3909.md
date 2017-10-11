---
title: "編譯器錯誤 C3909 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5cb5929fe1619ce75a7bde15ac08955247f1af7a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3909"></a>編譯器錯誤 C3909
aWinRT 或 managed 的事件宣告必須發生在 WinRT 或 managed 的類型  
  
 在原生類型中宣告 Windows 執行階段事件或 managed 事件。 若要修正這個錯誤，請在 Windows 執行階段類型或 managed 類型中宣告事件。  
  
 如需詳細資訊，請參閱[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下列範例會產生 C3909，並顯示如何修正此問題：  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```
