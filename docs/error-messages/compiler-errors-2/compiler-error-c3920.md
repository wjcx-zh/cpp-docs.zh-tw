---
title: 編譯器錯誤 C3920 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85638907f350eb3545a858f1319e56b2459f09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112703"
---
# <a name="compiler-error-c3920"></a>編譯器錯誤 C3920

' 運算子 ': 無法定義後置遞增/遞減 WinRT 或 CLR 運算子。 呼叫後置 WinRT 或 CLR 運算子將會呼叫對應的前置 WinRT 或 CLR 運算子 (op_Increment/op_Decrement)，但其具有後置語意

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