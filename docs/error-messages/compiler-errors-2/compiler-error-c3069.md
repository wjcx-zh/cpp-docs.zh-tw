---
title: 編譯器錯誤 C3069
ms.date: 11/04/2016
f1_keywords:
- C3069
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
ms.openlocfilehash: 230d2569ea314bde2ea9ef0c4fc58d1a9743807f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749512"
---
# <a name="compiler-error-c3069"></a>編譯器錯誤 C3069

'operator': 不可使用於列舉類型

CLR 列舉不支援運算子  如需詳細資訊，請參閱[如何：在/cli 中C++定義和使用](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)列舉。

## <a name="example"></a>範例

下列範例會產生 C3069：

```cpp
// C3069.cpp
// compile with: /clr
enum struct E { e1 };
enum F { f1 };

int main() {
   E e = E::e1;
   bool tf;
   tf = !e;   // C3069

   // supported for native enums
   F f = f1;
   tf = !f;
}
```
