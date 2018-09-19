---
title: 編譯器錯誤 C3246 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3246
dev_langs:
- C++
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a588067fa21e0aeee54516bcec28cdf3648ac9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047807"
---
# <a name="compiler-error-c3246"></a>編譯器錯誤 C3246

'class': 無法繼承自 'type'，因為它已經宣告為 'sealed'

標示為 [sealed](../../windows/sealed-cpp-component-extensions.md) 的類別不能當成任何其他類別的基底類別。

下列範例會產生 C3246：

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
