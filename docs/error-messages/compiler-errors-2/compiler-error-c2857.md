---
title: 編譯器錯誤 C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201847"
---
# <a name="compiler-error-c2857"></a>編譯器錯誤 C2857

> 在原始程式檔中找不到以/Yc*filename*命令列選項指定的 ' #include ' 語句

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項指定所要編譯之原始程式檔中未包含的 include 檔案名稱。

## <a name="remarks"></a>備註

當您在原始程式檔上使用 **/yc**<em>filename</em>選項來建立先行編譯標頭檔（PCH）時，該原始程式檔必須包含*filename*標頭檔。 包含在 PCH 檔案中的來源檔案所包含的每個檔案（包括指定的*檔案名*）。 在使用 **/yu**<em>filename</em>選項所編譯的其他原始程式檔中使用 PCH 檔案時，*檔案名*的包含必須是檔案中的第一個非批註行。 編譯器會在來源檔案中忽略任何專案，然後才會包含。

這個錯誤可能是因為未在 PCH 原始程式檔中編譯的條件式編譯區塊中的 `#include "filename"` 語句所造成。

## <a name="example"></a>範例

在一般用法中，專案中的一個原始程式檔會指定為 PCH 原始程式檔，而一個標頭檔會當做 PCH 標頭檔使用。 一般的 PCH 標頭檔包含專案中使用的所有程式庫標頭，但不是仍在開發的本機標頭。 在此範例中，會將 PCH 標頭檔命名為*my_pch .h*。

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

PCH 原始程式檔是使用 **/yc**<em>my_pch .h</em>選項來編譯。 如果編譯器找不到此 PCH 標頭檔的包含，則會產生 C2857：

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

若要使用此 PCH 檔案，必須使用 **/yu**<em>my_pch. h</em>選項來編譯來源檔案。 PCH 標頭檔必須先包含在使用 PCH 的原始程式檔中：

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```
