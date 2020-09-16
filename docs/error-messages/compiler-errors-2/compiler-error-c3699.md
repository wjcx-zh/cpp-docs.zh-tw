---
title: 編譯器錯誤 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: d313168e8033395da1749e000e52421939f77af4
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686648"
---
# <a name="compiler-error-c3699"></a>編譯器錯誤 C3699

' operator '：不能在類型 ' type ' 上使用這個間接取值

嘗試使用不允許的間接取值 `type` 。

## <a name="examples"></a>範例

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

簡單的屬性不能有參考型別。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md) 。 下列範例會產生 C3699。

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

「指標指標」語法相當於追蹤參考的控制碼。 下列範例會產生 C3699。

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
