---
title: 編譯器錯誤 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518088"
---
# <a name="compiler-error-c3622"></a>編譯器錯誤 C3622

'class': 類別宣告為 'keyword' 無法具現化

嘗試將類別標示為具現化[抽象](../../windows/abstract-cpp-component-extensions.md)。 類別標記為`abstract`可做為基底類別，但它無法具現化。

## <a name="example"></a>範例

下列範例會產生 C3622。

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
