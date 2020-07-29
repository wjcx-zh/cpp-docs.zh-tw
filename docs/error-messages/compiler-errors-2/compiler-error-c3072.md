---
title: 編譯器錯誤 C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: bcf2548fbe1182f7f6c4bd966ca6aa9ef9f10089
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212601"
---
# <a name="compiler-error-c3072"></a>編譯器錯誤 C3072

> 運算子 '*operator-name*' 不能套用至 ref 類別的實例

使用一元*運算子名稱*運算子，將 ref 類別的實例轉換為控制碼類型

CLR 類型需要 CLR 運算子，而不是原生（或標準）運算子。  如需詳細資訊，請參閱[追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3072。

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
