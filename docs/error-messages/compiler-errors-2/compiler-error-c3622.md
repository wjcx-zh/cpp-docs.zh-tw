---
title: 編譯器錯誤 C3622 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ba39a2baf9da2039bbc97fe459f8840effacea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062406"
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
