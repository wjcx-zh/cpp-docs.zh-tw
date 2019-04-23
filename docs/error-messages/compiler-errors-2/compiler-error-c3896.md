---
title: 編譯器錯誤 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 00e103720dc666b17566b67da19d4e908bb3addd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776076"
---
# <a name="compiler-error-c3896"></a>編譯器錯誤 C3896

'member': 不正確的初始設定式： 這個常值資料成員只能與 'nullptr' 初始化

A[常值](../../extensions/literal-cpp-component-extensions.md)資料成員未正確初始化。  請參閱[nullptr](../../extensions/nullptr-cpp-component-extensions.md)如需詳細資訊。

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