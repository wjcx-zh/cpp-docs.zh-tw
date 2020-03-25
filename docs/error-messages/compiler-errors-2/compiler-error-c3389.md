---
title: 編譯器錯誤 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201132"
---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389

> __declspec （*關鍵字*）不能搭配/clr： pure 或/clr： safe 使用

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

使用的[__declspec](../../cpp/declspec.md)修飾詞表示每個進程狀態。  [/clr： pure](../../build/reference/clr-common-language-runtime-compilation.md)意指每個[appdomain](../../cpp/appdomain.md)的狀態。  因此，不允許使用 `keyword`的 **__declspec**修飾詞來宣告變數，並以 **/clr： pure**進行編譯。

## <a name="example"></a>範例

下列範例會產生 C3389：

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
