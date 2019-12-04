---
title: 編譯器錯誤 C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 25023277258d33ab77bde18f6cdfabc862f50a63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741738"
---
# <a name="compiler-error-c3821"></a>編譯器錯誤 C3821

' function '： managed 類型或函數不能用在非受控函式中

具有內嵌元件或[setjmp](../../c-runtime-library/reference/setjmp.md)的函式不能包含實數值型別或 managed 類別。 若要修正這個錯誤，請移除內嵌元件，並 `setjmp` 或移除受管理的物件。

如果您嘗試在 vararg 函式中使用自動儲存，也可能會發生 C3821。  如需詳細資訊，請參閱[Variable 引數清單（...）C++（/cli）](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)和[ C++參考型別的堆疊語義](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3821。

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>範例

下列範例會產生 C3821。

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
