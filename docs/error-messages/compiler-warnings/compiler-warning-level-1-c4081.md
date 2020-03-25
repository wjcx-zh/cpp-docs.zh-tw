---
title: 編譯器警告 (層級 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: b882fe9c83f072c06a63733870f610549b209691
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200268"
---
# <a name="compiler-warning-level-1-c4081"></a>編譯器警告 (層級 1) C4081

必須是 'token1'; 但找到 'token2'

編譯器必須是這個內容中的不同語彙基元。

## <a name="example"></a>範例

```cpp
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```
