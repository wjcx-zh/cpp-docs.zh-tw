---
title: 編譯器錯誤 C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302536"
---
# <a name="compiler-error-c2356"></a>編譯器錯誤 C2356

初始設定區段不可以變更在轉譯單位

可能的原因：

- `#pragma init_seg` 加上區段初始化程式碼

- `#pragma init_seg` 加上另一個 `#pragma init_seg`

若要解決，請前往模組開頭中的區段初始化程式碼。 如果必須初始化多個區域，其移至個別的模組。

下列範例會產生 C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```