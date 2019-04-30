---
title: 編譯器錯誤 C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: e12f6e318d51ecaccc7c29e1e01d1aedcaac937e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404206"
---
# <a name="compiler-error-c3065"></a>編譯器錯誤 C3065

在非類別範圍不允許屬性宣告

[屬性](../../cpp/property-cpp.md) __declspec 修飾詞用在類別外部。  屬性只能在類別內宣告。

下列範例會產生 C3065：

```
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```