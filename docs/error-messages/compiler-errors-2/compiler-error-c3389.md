---
title: 編譯器錯誤 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 8a040e649074e115b1b86ea56db6c9ef48f4c0d0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520469"
---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389

> __declspec （*關鍵字*）不能搭配/clr： pure 或/clr： safe 使用

## <a name="remarks"></a>備註

**`/clr:pure`** 和 **`/clr:safe`** 編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

[`__declspec`](../../cpp/declspec.md)使用的修飾詞表示每個進程的狀態。  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md)意指每個 [`appdomain`](../../cpp/appdomain.md) 狀態。  因此，不允許使用*關鍵字*修飾詞宣告變數 **`__declspec`** ，並使用進行編譯 **`/clr:pure`** 。

## <a name="example"></a>範例

下列範例會產生 C3389：

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
