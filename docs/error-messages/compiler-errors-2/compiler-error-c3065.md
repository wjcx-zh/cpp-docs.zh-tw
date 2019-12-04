---
title: 編譯器錯誤 C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: 026a6d5191f5bf7969dd2c8217b624d44b8ca345
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761425"
---
# <a name="compiler-error-c3065"></a>編譯器錯誤 C3065

在非類別範圍不允許屬性宣告

[屬性](../../cpp/property-cpp.md) __declspec 修飾詞用在類別外部。  屬性只能在類別內宣告。

下列範例會產生 C3065：

```cpp
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```
