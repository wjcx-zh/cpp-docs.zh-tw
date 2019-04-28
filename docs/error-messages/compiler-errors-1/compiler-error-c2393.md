---
title: 編譯器錯誤 C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302393"
---
# <a name="compiler-error-c2393"></a>編譯器錯誤 C2393

> '*符號*': per-appdomain 符號不可配置在區段'*區段*'

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

使用[appdomain](../../cpp/appdomain.md)變數表示您使用編譯 **/clr: pure**或 **/clr: safe**，而且安全或純粹的映像不能包含資料區段。

請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C2393。 若要修正此問題，不會建立資料區段。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```