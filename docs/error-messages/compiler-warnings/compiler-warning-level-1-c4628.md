---
title: 編譯器警告（層級1） C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: 6063755db5ac517d868bc47d2c417356ccef5d58
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051434"
---
# <a name="compiler-warning-level-1-c4628"></a>編譯器警告（層級1） C4628

不支援使用 -Ze 的雙拼詞。 字元順序 'digraph' 沒有解譯為 'char' 的替代語彙基元 (Token)

[/Ze](../../build/reference/za-ze-disable-language-extensions.md)下不支援 Digraphs。 此警告後面會接著錯誤。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4628：

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```