---
title: 編譯器錯誤 C3671 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3671
dev_langs:
- C++
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50b52bb30b24204e810dc350cdb7fef502a93852
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263631"
---
# <a name="compiler-error-c3671"></a>編譯器錯誤 C3671
'function_1': 函式不會覆寫 'function_2'  
  
 使用明確覆寫語法時，編譯器會產生錯誤，如果函式不會覆寫。  請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3671。  
  
```  
// C3671.cpp  
// compile with: /clr /c  
ref struct S {  
   virtual void f();  
};  
  
ref struct S1 : S {  
   virtual void f(int) new sealed = S::f;   // C3671  
   virtual void f() new sealed = S::f;  
};  
```