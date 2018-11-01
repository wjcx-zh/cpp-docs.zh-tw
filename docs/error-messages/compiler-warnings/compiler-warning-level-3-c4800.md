---
title: 編譯器警告 (層級 3) C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636133"
---
# <a name="compiler-warning-level-3-c4800"></a>編譯器警告 (層級 3) C4800

> '*型別*': 值強制設 bool 'true' 或 'false' （效能警告）

值，並不會產生這個警告`bool`已指派或強制轉型為型別`bool`。 一般而言，會產生此訊息指派`int`變數，以`bool`變數位置`int`變數只包含值 **，則為 true**和**false**，而且可能會宣告類型為`bool`。 如果您不能重新撰寫運算式，以使用型別`bool`，然後您可以新增 「`!=0`」 運算式，可讓運算式型別`bool`。 將運算式轉換成輸入`bool`不停用警告，這是設計所致。

在 Visual Studio 2017 不會再產生這個警告。

## <a name="example"></a>範例

下列範例會產生 C4800，並示範如何修正此問題：

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```