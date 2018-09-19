---
title: 呼叫範例： 函式原型和呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04e681560854be4c93b1c93786d38771c07244ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099573"
---
# <a name="calling-example-function-prototype-and-call"></a>呼叫範例：函式原型和呼叫

## <a name="microsoft-specific"></a>Microsoft 特定的

下列範例示範使用各種呼叫慣例執行函式呼叫的結果。

這個範例是以下列函式架構為基礎。 以適當的呼叫慣例取代 `calltype`。

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

如需詳細資訊，請參閱 <<c0> [ 呼叫結果範例](../cpp/results-of-calling-example.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)