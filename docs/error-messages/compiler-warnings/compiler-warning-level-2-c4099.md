---
title: 編譯器警告 (層級 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471717"
---
# <a name="compiler-warning-level-2-c4099"></a>編譯器警告 (層級 2) C4099

'identifier': 第一次出現 使用 'objecttype1'，之後現在發現使用 'objecttype2' 的類型名稱

宣告為結構的物件定義為類別，或宣告為類別的物件定義為結構。 編譯器會使用在定義中指定的類型。

## <a name="example"></a>範例

下列範例會產生 C4099。

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```