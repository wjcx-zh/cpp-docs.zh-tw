---
title: 編譯器警告 （層級 1） C4628 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4628
dev_langs:
- C++
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36b3f7e65a6235b7eb890cf1265b949760f370ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082556"
---
# <a name="compiler-warning-level-1-c4628"></a>編譯器警告 (層級 1) C4628

不支援使用 -Ze 的雙拼詞。 字元順序 'digraph' 沒有解譯為 'char' 的替代語彙基元 (Token)

不支援的雙拼詞[/Ze](../../build/reference/za-ze-disable-language-extensions.md)。 這個警告後面會接著錯誤。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4628:

```
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```