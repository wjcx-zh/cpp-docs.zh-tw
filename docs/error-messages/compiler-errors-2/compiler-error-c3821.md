---
title: 編譯器錯誤 C3821 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e1f9a0bbb8eaae6b316b3d00e4201b2b64222ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023029"
---
# <a name="compiler-error-c3821"></a>編譯器錯誤 C3821

'function': managed 的類型或函式不能用於 unmanaged 函式

具有內嵌組譯碼的函式或[setjmp](../../c-runtime-library/reference/setjmp.md)不能包含實值型別或 managed 的類別。 若要修正這個錯誤，請移除內嵌組譯碼和`setjmp`或移除受管理的物件。

如果您嘗試使用 vararg 函式中的自動儲存體，也會發生 C3821。  如需詳細資訊，請參閱[變數引數清單 （...）(C + + /CLI CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)並[參考類型的 c + + 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3821。

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>範例

下列範例會產生 C3821。

```
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
