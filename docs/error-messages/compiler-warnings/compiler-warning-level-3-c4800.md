---
title: 編譯器警告 （層級 4） C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: a901c4acbfc80ca10663d37c09921f04c5b6dd17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58142585"
---
# <a name="compiler-warning-level-4-c4800"></a>編譯器警告 （層級 4） C4800

::: moniker range=">= vs-2019"
2019 和更新版本的 visual Studio:
> 隱含的轉換，從 '*型別*' 為 bool。 可能導致資訊遺失
::: moniker-end

C4800 是層級 3 警告，在 Visual Studio 2015 和更早版本：
> '*型別*': 值強制設 bool 'true' 或 'false' （效能警告）

值，會隱含地轉換成類型時，會產生這個警告`bool`。 一般而言，會產生此訊息指派`int`變數，以`bool`變數位置`int`變數只包含值 **，則為 true**和**false**，而且可能會宣告類型為`bool`。 如果您不能重新撰寫運算式，以使用型別`bool`，然後您可以新增 「`!=0`」 運算式，可讓運算式型別`bool`。 將運算式轉換成輸入`bool`不會停用警告，這是設計所致。

::: moniker range=">= vs-2017"
Visual Studio 2017 中，不會發出這個警告。
::: moniker-end

::: moniker range=">= vs-2019"
從 Visual Studio 2019 的預設為關閉此警告。 使用 __/w__*n*__4800__若要啟用當做層級的 C4800 *n*警告，或[/wall](../../build/reference/compiler-option-warning-level.md)啟用所有警告，預設為關閉的。 如需詳細資訊，請參閱 <<c0> [ 編譯器警告，是 Off By Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
::: moniker-end

## <a name="example"></a>範例

下列範例會產生 C4800，並示範如何修正此問題：

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