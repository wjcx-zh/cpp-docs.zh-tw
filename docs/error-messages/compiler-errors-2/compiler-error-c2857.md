---
title: 編譯器錯誤 C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 10c0ea3b54ded29bf80f83713cea33428dca6ca0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350435"
---
# <a name="compiler-error-c2857"></a>編譯器錯誤 C2857

> '#include' 陳述式指定 /Yc*filename*原始程式檔中找不到命令列選項

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項會指定不會納入要編譯的原始程式檔的 include 檔案的名稱。

## <a name="remarks"></a>備註

當您使用 **/Yc**<em>filename</em>建立的先行編譯標頭 (PCH) 檔案，來源檔案的原始程式檔的選項必須包含*filename*標頭檔。 包含原始程式檔，包括指定每個檔案*filename*，會包含在 PCH 檔案。 使用編譯的其他原始程式檔中 **/Yu**<em>filename</em>選項可使用 PCH 檔案時，將包含的*filename*必須是第一個非註解列在檔案中的。 編譯器會忽略包括之前的原始程式檔中的任何項目。

此錯誤可能因`#include "filename"`就不會編譯在 PCH 原始程式檔中的條件式編譯區塊中的陳述式。

## <a name="example"></a>範例

典型的用法，在您的專案中的一個原始程式檔已指定為 PCH 的來源檔案，且一個標頭檔做為 PCH 標頭檔。 典型的 PCH 標頭檔會有的所有程式庫標頭用於您的專案，但仍在開發的非本機標頭。 在此範例中，名為 PCH 標頭檔*my_pch.h*。

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

PCH 原始程式檔來編譯 **/Yc**<em>my_pch.h</em>選項。 如果編譯器找不到包含此 PCH 標頭檔，它會產生 C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

若要使用此 PCH 檔案，必須編譯原始程式檔所 **/Yu**<em>my_pch.h</em>選項。 PCH 標頭檔必須包含第一次，在使用 PCH 的原始程式檔：

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