---
title: 編譯器警告 （層級 1 和 4） C4112 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9015a7ee7a0b71d3c6aafd3e3b32d4ea1b07f108
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110545"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>編譯器警告 (層級 1 和 4) C4112

\#列必須有介於 1 和數字之間的整數

[#line](../../preprocessor/hash-line-directive-c-cpp.md) 指示詞會指定超過允許範圍的整數參數。

如果指定的參數小於 1，行計數器就會重設為 1。 如果指定的參數大於編譯器定義限制的 *數字*，行計數器不會變更。 這是 ANSI 相容性層級 1 警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 擴充功能的層級 4 警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

下列範例會產生 C4112：

```
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```