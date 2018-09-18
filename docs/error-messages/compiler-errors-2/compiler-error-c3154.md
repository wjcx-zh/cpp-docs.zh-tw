---
title: 編譯器錯誤 C3154 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3154
dev_langs:
- C++
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92a888020e306e762ffb242cb92636cc14680bf5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074652"
---
# <a name="compiler-error-c3154"></a>編譯器錯誤 C3154

必須是 '、' 省略符號之前。 非逗號分隔的省略符號參數陣列函式不支援。

變數引數的函式宣告不正確。

如需詳細資訊，請參閱[變數引數清單 （...）(C + + /CLI CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

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