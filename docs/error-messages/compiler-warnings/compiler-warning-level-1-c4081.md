---
title: 編譯器警告 (層級 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: f43a736a73b4a504755cd8dc079a41e59aaf72bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363423"
---
# <a name="compiler-warning-level-1-c4081"></a>編譯器警告 (層級 1) C4081

必須是 'token1'; 但找到 'token2'

編譯器必須是這個內容中的不同語彙基元。

## <a name="example"></a>範例

```
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```