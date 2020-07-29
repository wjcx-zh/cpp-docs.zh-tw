---
title: 編譯器警告 (層級 2 和 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: ab51b16331cc6a102c828234d2c2b8be84f2d276
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225237"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>編譯器警告 (層級 2 和 3) C4008

'identifier': 已忽略 'attribute' 屬性

編譯器已忽略函 **`__fastcall`** 式 **`static`** **`inline`** （層級3警告）或資料（層級2警告）的、或屬性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. **`__fastcall`** 具有資料的屬性。

1. **`static`** 或 **`inline`** 具有**main**函式的屬性。
