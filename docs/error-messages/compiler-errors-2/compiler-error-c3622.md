---
title: 編譯器錯誤 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 8775ff6fd78f1092ae931921a2b15ed2f8b166e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214538"
---
# <a name="compiler-error-c3622"></a>編譯器錯誤 C3622

' class '：無法具現化宣告為 ' 關鍵字 ' 的類別

嘗試具現化標示為[abstract](../../extensions/abstract-cpp-component-extensions.md)的類別。 標記為的類別 **`abstract`** 可以是基類，但無法具現化。

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
