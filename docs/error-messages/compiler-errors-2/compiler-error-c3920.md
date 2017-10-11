---
title: "編譯器錯誤 C3920 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2e2bf82de4e32c2b0ae586c78c69ce474947c3ec
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3920"></a>編譯器錯誤 C3920
' 運算子 ': 無法定義後置遞增/遞減 WinRT 或 CLR 運算子。 呼叫後置 WinRT 或 CLR 運算子將會呼叫對應的前置 WinRT 或 CLR 運算子 (op_Increment/op_Decrement)，但是會具有後置語意  
  
 Windows 執行階段和 CLR 不支援後置運算子，而且不允許使用者定義的後置運算子。  您可以定義前置運算子，而且前置運算子將用於前置和後置遞增作業。  
  
 下列範例會產生 C3920，並顯示如何修正它：  
  
```  
// C3920.cpp  
// compile with: /clr /LD  
public value struct V {  
   static V operator ++(V me, int)  
   // try the following line instead  
   // static V operator ++(V me)  
   {   // C3920  
      me.m_i++;  
      return me;  
   }  
  
   int m_i;  
};  
  
```
