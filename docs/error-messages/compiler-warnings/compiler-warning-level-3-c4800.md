---
title: 編譯器警告（層級4） C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: a516be2e6e1966c3249ed21cc6d480ddea8b5ec1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220011"
---
# <a name="compiler-warning-level-4-c4800"></a>編譯器警告（層級4） C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 及更新版本：
> 從 '*type*' 隱含轉換為 bool。 可能遺失資訊
::: moniker-end

C4800 是 Visual Studio 2015 和更早版本中的層級3警告：
> '*type*'：強制將值設為 bool ' true ' 或 ' false ' （效能警告）

當值隱含地轉換成類型時，就會產生這個警告 **`bool`** 。 通常，此訊息是由 **`int`** 將變數指派給變數， **`bool`** 其中 **`int`** 變數只包含值 **`true`** 和 **`false`** ，而且可以重新宣告為類型 **`bool`** 。 如果您無法將運算式重寫為使用類型 **`bool`** ，則可以在 `!=0` 運算式中加入 ""，以提供運算式類型 **`bool`** 。 將運算式轉換成類型 **`bool`** 並不會停用警告，這是設計的。

::: moniker range=">= vs-2017"
Visual Studio 2017 不會發出此警告。
::: moniker-end

::: moniker range=">= vs-2019"
從 Visual Studio 2019 開始，預設會關閉此警告。 使用 __/w__*n*__4800__ ，讓 C4800 成為層級*n*警告，或[/Wall](../../build/reference/compiler-option-warning-level.md)來啟用所有預設為關閉的警告。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
::: moniker-end

## <a name="example"></a>範例

下列範例會產生 C4800，並顯示如何修正此問題：

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```
