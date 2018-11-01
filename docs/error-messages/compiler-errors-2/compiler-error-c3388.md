---
title: 編譯器錯誤 C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 1f6e51542cc852543d648f9f94a964ae0cab3b30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512661"
---
# <a name="compiler-error-c3388"></a>編譯器錯誤 C3388

'type': 不允許作為條件約束，假設是 'ref class' 以繼續剖析

已在泛型類型上指定條件約束，但未正確地指定條件約束。 請參閱[泛型類型參數的條件約束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3388。

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```