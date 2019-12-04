---
title: 編譯器錯誤 C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760175"
---
# <a name="compiler-error-c3288"></a>編譯器錯誤 C3288

' type '：控制碼類型的取消參考不合法

編譯器偵測到控制碼類型的非法取值。 您可以對控制碼型別進行取值，並將它指派給參考。 如需詳細資訊，請參閱[追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3288。

```cpp
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```
