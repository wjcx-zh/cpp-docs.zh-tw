---
title: 編譯器錯誤 C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: e40b0c2a56c36b92465fb3bb3451a48c88b5822e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745922"
---
# <a name="compiler-error-c3154"></a>編譯器錯誤 C3154

在省略號前面必須是 '，'。 參數陣列函式不支援非逗號分隔的省略號。

變數引數函數未正確宣告。

如需詳細資訊，請參閱[Variable 引數清單（...）C++（/cli）](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3154。

```cpp
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```
