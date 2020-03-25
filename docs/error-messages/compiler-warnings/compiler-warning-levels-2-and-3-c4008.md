---
title: 編譯器警告 (層級 2 和 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198000"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>編譯器警告 (層級 2 和 3) C4008

'identifier': 已忽略 'attribute' 屬性

編譯器已忽略函式 (層級 3 警告) 或資料 (層級 2 警告) 的 `__fastcall`、 **static**或 **inline** 屬性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 具有資料的`__fastcall` 屬性。

1. 具有**inline** 函式的 **static** 或 **inline** 屬性。
