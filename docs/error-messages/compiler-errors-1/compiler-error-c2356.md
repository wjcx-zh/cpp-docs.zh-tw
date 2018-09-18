---
title: 編譯器錯誤 C2356 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfad1703b36e1cd995207d35b99b323c883f828
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065409"
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