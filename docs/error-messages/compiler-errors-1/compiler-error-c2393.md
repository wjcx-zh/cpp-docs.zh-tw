---
title: 編譯器錯誤 C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: cc3c124f1a4daea0f2517a93c6b354b8233aa5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205981"
---
# <a name="compiler-error-c2393"></a>編譯器錯誤 C2393

> '*symbol*'：無法在區段 '*segment*' 中配置每個 appdomain 的符號

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

使用[appdomain](../../cpp/appdomain.md)變數表示您是使用 **/clr： pure**或 **/clr： safe**進行編譯，而安全或純影像則不能包含資料區段。

如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md) 。

## <a name="example"></a>範例

下列範例會產生 C2393。 若要修正此問題，請勿建立資料區段。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
