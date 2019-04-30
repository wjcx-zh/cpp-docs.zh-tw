---
title: 編譯器錯誤 C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: fb6d228826cf1b21904863505c0963069e89d32d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344872"
---
# <a name="compiler-error-c2378"></a>編譯器錯誤 C2378

'identifier' : 重複定義; 符號無法以 typedef 多載

識別項已重新定義為 `typedef`。

下列範例會產生 C2378：

```
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```