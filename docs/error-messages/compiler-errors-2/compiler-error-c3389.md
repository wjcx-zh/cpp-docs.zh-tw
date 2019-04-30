---
title: 編譯器錯誤 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402576"
---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389

> __declspec (*關鍵字*) 不能以 /clr: pure 或 /clr: safe

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

A [__declspec](../../cpp/declspec.md)修飾詞表示每個處理序狀態。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)表示每個[appdomain](../../cpp/appdomain.md)狀態。  因此，宣告的變數`keyword` **__declspec**修飾詞和編譯 **/clr: pure**不允許。

## <a name="example"></a>範例

下列範例會產生 C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```