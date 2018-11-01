---
title: 編譯器錯誤 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: e413e4a08ce22ef109179ff0f98baf32ebba41c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525821"
---
# <a name="compiler-error-c3699"></a>編譯器錯誤 C3699

'operator': 類型 'type' 上無法使用這個間接取值

嘗試使用不允許的間接取值`type`。

## <a name="example"></a>範例

下列範例會產生 C3699。

```
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

Trivial 屬性不能有參考類型。 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。 下列範例會產生 C3699。

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>範例

相當於"指標的指標 」 語法是追蹤參考的控制代碼。 下列範例會產生 C3699。

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```