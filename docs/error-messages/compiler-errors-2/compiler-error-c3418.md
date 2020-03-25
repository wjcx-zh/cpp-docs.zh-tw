---
title: 編譯器錯誤 C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 21023bfb551a1894e25cc4940892dde0f0440a0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200873"
---
# <a name="compiler-error-c3418"></a>編譯器錯誤 C3418

不支援存取規範 'specifier'

CLR 存取規範指定不正確。  如需詳細資訊，請參閱[如何：定義和使用類別和結構C++（/cli）](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)中的類型可見度和成員可見度。

## <a name="example"></a>範例

下列範例會產生 C3418：

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```
