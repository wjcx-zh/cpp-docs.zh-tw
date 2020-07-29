---
title: 編譯器警告 (層級 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: 8742fd5e64f2ba1877fa3fbecfb221ef295d463e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219894"
---
# <a name="compiler-warning-level-4-c4289"></a>編譯器警告 (層級 4) C4289

使用非標準的擴充：'var' : 在 for-loop 範圍外使用 for-loop 中所宣告的迴圈控制變數

以[/ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc： forScope-** 進行編譯時，會在-loop 範圍之後使用[for](../../cpp/for-statement-cpp.md)迴圈中宣告的變數 **`for`** 。

如需如何在迴圈中以/Ze 指定標準行為的資訊，請參閱[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) **`for`** ** **。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4289：

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```
