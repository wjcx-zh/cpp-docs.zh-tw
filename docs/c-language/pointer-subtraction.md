---
title: 指標減法 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer subtraction
ms.assetid: 4d515690-088a-43f6-bb8c-57b849f7ccf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9756861fd1204a05179ac77dfa648822ed83e5a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079529"
---
# <a name="pointer-subtraction"></a>指標減法

**ANSI 3.3.6、4.1.1**：用來保存相同陣列兩個元素指標之間差異的整數類型，即 **ptrdiff_t**

`ptrdiff_t` typedef 在 32 位元 x86 平台上是 `int`。 在 64 位元平台上，`ptrdiff_t` typedef 為 `__int64`。

## <a name="see-also"></a>請參閱

[陣列和指標](../c-language/arrays-and-pointers.md)
