---
title: 編譯器警告 (層級 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544062"
---
# <a name="compiler-warning-level-1-c4399"></a>編譯器警告 (層級 1) C4399

> '*符號*': __declspec （dllimport） 以 /clr 編譯時不應該標示處理序專屬符號： pure

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

原生映像或 CLR 建構與原生映像中的資料不匯入到純映像。 若要解決這個警告，以編譯 **/clr** (不 **/clr: pure**) 或刪除`__declspec(dllimport)`。

## <a name="example"></a>範例

下列範例會產生 C4399。

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```