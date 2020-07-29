---
title: 編譯器警告 (層級 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: efe021c9994e20f2630e31537bcc6099783b4308
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219998"
---
# <a name="compiler-warning-level-4-c4062"></a>編譯器警告 (層級 4) C4062

> 未處理列舉 '*enumeration*' 之 switch 中的列舉值 '*identifier*'

列舉值*識別碼*在語句中沒有相關聯的 `case` 處理常式 **`switch`** ，而且沒有 **`default`** 可攔截它的標籤。 遺漏的情況可能是監督，而且是您程式碼中可能發生的錯誤。 如需具有案例的語句中未使用之枚舉器的相關警告 **`switch`** **`default`** ，請參閱[C4061](compiler-warning-level-4-c4061.md)。

此警告預設為關閉。 如需如何啟用預設為關閉之警告的詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>範例

下列範例會產生 C4062，並顯示如何修正此問題：

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>另請參閱

[編譯器警告（層級4） C4061](compiler-warning-level-4-c4061.md)
