---
title: 編譯器警告 (層級 1 和 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: f614373e1b96de2c8167d7981c0a87a4e1c58435
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991237"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>編譯器警告 (層級 1 和 4) C4112

\#行需要介於1到數位之間的整數

[#line](../../preprocessor/hash-line-directive-c-cpp.md) 指示詞會指定超過允許範圍的整數參數。

如果指定的參數小於 1，行計數器就會重設為 1。 如果指定的參數大於編譯器定義限制的 *數字*，行計數器不會變更。 這是 ANSI 相容性層級 1 警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 擴充功能的層級 4 警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

下列範例會產生 C4112：

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```
