---
title: 編譯器錯誤 C3069
ms.date: 11/04/2016
f1_keywords:
- C3069
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
ms.openlocfilehash: 6c6451d31da2bb708d3f233225be713981b062e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406752"
---
# <a name="compiler-error-c3069"></a>編譯器錯誤 C3069

'operator': 不可使用於列舉類型

CLR 列舉不支援運算子  如需詳細資訊，請參閱[如何：定義和使用列舉在C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3069：

```
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