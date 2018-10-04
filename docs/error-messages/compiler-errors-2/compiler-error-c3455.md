---
title: 編譯器錯誤 C3455 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3455
dev_langs:
- C++
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a10c91f34cd00b8524a047131e9a39b901c83fce
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788587"
---
# <a name="compiler-error-c3455"></a>編譯器錯誤 C3455

'attribute': 沒有任何屬性建構函式與引數相符

用來宣告屬性的值無效。  請參閱[屬性](../../windows/attributes/attribute.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3455。

```
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```