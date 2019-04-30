---
title: 編譯器錯誤 C3204
ms.date: 11/04/2016
f1_keywords:
- C3204
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
ms.openlocfilehash: 4c34ad35916f01323a72102c7099d4afd0ab17be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402719"
---
# <a name="compiler-error-c3204"></a>編譯器錯誤 C3204

無法從 catch 區塊呼叫 '_alloca'

當您在 catch 區塊內使用 [_alloca](../../c-runtime-library/reference/alloca.md) 呼叫時，會發生這個錯誤。

## <a name="example"></a>範例

下列範例會產生 C3204：

```
// C3204.cpp
// compile with: /EHsc
#include <malloc.h>

void ShowError(void)
{
   try
   {
   }
   catch(...)
   {
      _alloca(1);   // C3204
   }
}
```