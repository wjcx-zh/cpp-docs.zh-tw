---
title: 編譯器錯誤 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781909"
---
# <a name="compiler-error-c3622"></a>編譯器錯誤 C3622

'class': 類別宣告為 'keyword' 無法具現化

嘗試將類別標示為具現化[抽象](../../extensions/abstract-cpp-component-extensions.md)。 類別標記為`abstract`可做為基底類別，但它無法具現化。

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
