---
title: 編譯器警告 (層級 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: affb2b5231d3745d4826e92657e355ec99570e7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199663"
---
# <a name="compiler-warning-level-1-c4628"></a>編譯器警告 (層級 1) C4628

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
