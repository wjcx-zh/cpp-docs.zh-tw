---
title: 編譯器錯誤 C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 2b76fa91d739e9cc89251aaf56aa9b196e62a68d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777125"
---
# <a name="compiler-error-c3072"></a>編譯器錯誤 C3072

運算子 'operator' 無法套用至 ref 類別的執行個體

使用一元 '`operator` ' 運算子，將 ref 類別的執行個體轉換為控制代碼類型

CLR 型別需要 CLR 運算子，not 原生 （或標準） 的運算子。  如需詳細資訊，請參閱 <<c0> [ 追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3072。

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```