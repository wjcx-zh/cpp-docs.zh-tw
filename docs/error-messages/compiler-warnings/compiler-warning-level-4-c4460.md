---
title: "編譯器警告 （層級 4） C4460 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4460
dev_langs:
- C++
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa925e8d0ef7779f21485cb154b9b9209ce2388e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4460"></a>編譯器警告 (層級 4) C4460
WinRT 或 CLR 運算子 'operator'，具有以傳址方式傳遞的參數。 WinRT 或 CLR 運算子 'operator' 具有來自 C++ 運算子 'operator' 的不同語意，您是否想要以傳值方式傳遞?  
  
 您以傳值方式傳遞到使用者定義的 Windows 執行階段或 CLR 運算子。 如果值在函式內有變更，請注意，函式呼叫後傳回的值將被指派函式的傳回值。 在標準 C++ 中，變更的值會在函式呼叫之後反映。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4460，並示範如何修正此問題。  
  
```  
// C4460.cpp  
// compile with: /W4 /clr   
#include <stdio.h>  
  
public value struct V {  
   static V operator ++(V& me) {   // C4460  
   // try the following line instead  
   // static V operator ++(V me) {  
  
      printf_s(__FUNCSIG__ " called\n");  
      V tmp = me;  
      me.m_i++;  
      return tmp;  
   }  
   int m_i;  
};  
  
int main() {  
   V v;  
   v.m_i = 0;  
  
   printf_s("%d\n", v.m_i);   // Should print 0  
   v++;   // Translates to "v = V::operator ++(v)"  
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning  
}  
```