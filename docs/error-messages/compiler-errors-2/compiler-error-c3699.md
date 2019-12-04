---
title: 編譯器錯誤 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758030"
---
# <a name="compiler-error-c3699"></a>編譯器錯誤 C3699

' operator '：無法在類型 ' type ' 上使用這個間接取值

嘗試使用 `type`上不允許的間接取值。

## <a name="example"></a>範例

下列範例會產生 C3699。

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>範例

一般屬性不能有參考型別。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md) 。 下列範例會產生 C3699。

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>範例

「指標」語法的對等項是追蹤參考的控制碼。 下列範例會產生 C3699。

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
