---
title: 編譯器錯誤 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 32aed1dfd957035cdd60fa97bd9ec534de03cb06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547930"
---
# <a name="compiler-error-c3896"></a>編譯器錯誤 C3896

'member': 不正確的初始設定式： 這個常值資料成員只能與 'nullptr' 初始化

A[常值](../../windows/literal-cpp-component-extensions.md)資料成員未正確初始化。  請參閱[nullptr](../../windows/nullptr-cpp-component-extensions.md)如需詳細資訊。

下列範例會產生 C3896:

```
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```