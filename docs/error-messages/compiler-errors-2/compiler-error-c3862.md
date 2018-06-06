---
title: 編譯器錯誤 C3862 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b21e457feb6d090e4abaf531293987eb3504457
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704967"
---
# <a name="compiler-error-c3862"></a>編譯器錯誤 C3862

> '*函式*': 無法編譯 unmanaged 函式以 /clr: pure 或 /clr: safe

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

編譯 **/clr: pure**或 **/clr: safe**會產生 MSIL 僅映像，沒有原生 (unmanaged) 程式碼的映像。  因此，您無法使用`unmanaged`pragma 中的 **/clr: pure**或 **/clr: safe**編譯。

如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。

## <a name="example"></a>範例

下列範例會產生 C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```