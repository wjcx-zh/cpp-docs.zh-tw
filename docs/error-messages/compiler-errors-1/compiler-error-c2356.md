---
title: 編譯器錯誤 C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759928"
---
# <a name="compiler-error-c2356"></a>編譯器錯誤 C2356

在轉譯單位期間，初始化區段不得變更

可能的原因:

- 前面加上區段初始化程式碼的 `#pragma init_seg`

- `#pragma init_seg` 前面加上另一個 `#pragma init_seg`

若要解決此問題，請將區段初始化程式碼移至模組的開頭。 如果必須初始化多個區域，請將它們移至不同的模組。

下列範例會產生 C2356：

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
