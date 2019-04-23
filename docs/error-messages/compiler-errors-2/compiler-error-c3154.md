---
title: 編譯器錯誤 C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: 9f7af4e19fab5f5a0539e9fc3bf9dbeffb5c6fbf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776284"
---
# <a name="compiler-error-c3154"></a>編譯器錯誤 C3154

必須是 '、' 省略符號之前。 非逗號分隔的省略符號參數陣列函式不支援。

變數引數的函式宣告不正確。

如需詳細資訊，請參閱[變數引數清單 （...）(C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>範例

下列範例會產生 C3154。

```
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