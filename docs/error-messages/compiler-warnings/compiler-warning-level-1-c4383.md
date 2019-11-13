---
title: 編譯器警告（層級1） C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 9681408841173bad4aca3305e727ddde6cd98f14
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966165"
---
# <a name="compiler-warning-level-1-c4383"></a>編譯器警告（層級1） C4383

' instance_dereference_operator '：當使用者定義的 ' operator ' 運算子存在時，對控制碼取值的意義可能會變更;將運算子撰寫為靜態函式，以明確瞭解運算元

當您在 managed 類型中加入取值運算子的使用者定義實例覆寫時，可能會覆寫類型之取值運算子的功能，以傳回控制碼的物件。 請考慮撰寫靜態的使用者定義取值運算子。

如需詳細資訊，請參閱[物件運算子的控制碼（^）](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)和[追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

此外，實例運算子無法透過參考的中繼資料提供給其他語言編譯器。 如需詳細資訊，請參閱[使用者定義的C++運算子（/cli）](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C4383。

```cpp
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```