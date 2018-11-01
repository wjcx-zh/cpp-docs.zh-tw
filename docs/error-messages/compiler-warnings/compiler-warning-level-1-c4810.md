---
title: 編譯器警告 (層級 1) C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: 4701ac40d436a9f5511f2c7cec86e8183ec2f837
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508126"
---
# <a name="compiler-warning-level-1-c4810"></a>編譯器警告 (層級 1) C4810

pragma pack(show) 的值 == n

當您使用 **pack** pragma 的 [show](../../preprocessor/pack.md) 選項時，會發出這個警告。 *n* 是目前的 pack 值。

例如，下列程式碼顯示 C4810 警告如何使用 pack pragma：

```
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```