---
title: 編譯器錯誤 C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 56eeac18d5b8efc32501bf54e2de3aa216e05a13
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742017"
---
# <a name="compiler-error-c3465"></a>編譯器錯誤 C3465

若要使用類型 'type'，您必須參考組件 'assembly'

在您重新編譯用戶端之前，類型轉送都適用於用戶端應用程式。 當您重新編譯時，您會需要每一個包含用戶端應用程式所用之類型定義之組件的參考。

如需詳細資訊，請參閱 [類型轉送 (c + +/cli) ](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="examples"></a>範例

下列範例會建置包含類型新位置的組件。

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

下列範例建置的組件，過去用於包含類型定義，現在包含類型的轉送語法。

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

下列範例會產生 C3465。

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
