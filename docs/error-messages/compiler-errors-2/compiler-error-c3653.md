---
title: 編譯器錯誤 C3653 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3653
dev_langs:
- C++
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a78dd5a9c52c9dfc845de43c62ae38180d0d079f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266457"
---
# <a name="compiler-error-c3653"></a>編譯器錯誤 C3653
'function': 不能當做具名覆寫： 覆寫未找到; 函式您是否忘記指明此函式明確地使用:: 運算子？  
  
 明確覆寫指定找不到任何介面中的函式。 如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下列範例會產生 C3653:  
  
```  
// C3653.cpp  
// compile with: /clr  
public interface struct I {  
   void h();  
};  
  
public ref struct X : public I {  
   virtual void f() new sealed = J {};   // C3653 no J in scope  
   virtual void g() {}   // OK  
   virtual void h() new sealed = I::h {};   // OK  
};  
```