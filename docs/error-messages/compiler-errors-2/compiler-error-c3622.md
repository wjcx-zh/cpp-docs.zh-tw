---
title: 編譯器錯誤 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740893"
---
# <a name="compiler-error-c3622"></a>編譯器錯誤 C3622

' class '：無法具現化宣告為 ' 關鍵字 ' 的類別

嘗試具現化標示為[abstract](../../extensions/abstract-cpp-component-extensions.md)的類別。 標記為 `abstract` 的類別可以是基類，但無法具現化。

## <a name="example"></a>範例

下列範例會產生 C3622。

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
