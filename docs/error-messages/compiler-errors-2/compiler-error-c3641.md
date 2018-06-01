---
title: 編譯器錯誤 C3641 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3641
dev_langs:
- C++
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99aef6bcfd8ac7ea89cb62fda37c7aec012e16de
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704941"
---
# <a name="compiler-error-c3641"></a>編譯器錯誤 C3641

> '*函式*': 無效的呼叫慣例 'calling_convention' 以 /clr 編譯的函式： pure 或 /clr: safe

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

只有[__clrcall](../../cpp/clrcall.md)呼叫慣例則允許使用[/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C3641:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```