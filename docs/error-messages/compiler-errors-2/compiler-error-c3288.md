---
title: 編譯器錯誤 C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: d076dabe0df91cefb90be5ec9e90f371331a51f1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776765"
---
# <a name="compiler-error-c3288"></a>編譯器錯誤 C3288

'type': 不合法取值 （dereference) 的控制代碼類型

編譯器偵測到不合法取值的控制代碼類型。 您可以控制代碼類型取值 （dereference），並將它指派給參考。 如需詳細資訊，請參閱 <<c0> [ 追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3288。

```
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