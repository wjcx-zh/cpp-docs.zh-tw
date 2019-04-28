---
title: 編譯器警告 (層級 2 和 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359965"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>編譯器警告 (層級 2 和 3) C4008

'identifier': 已忽略 'attribute' 屬性

編譯器已忽略函式 (層級 3 警告) 或資料 (層級 2 警告) 的 `__fastcall`、 **static**或 **inline** 屬性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 具有資料的`__fastcall` 屬性。

1. 具有**inline** 函式的 **static** 或 **inline** 屬性。