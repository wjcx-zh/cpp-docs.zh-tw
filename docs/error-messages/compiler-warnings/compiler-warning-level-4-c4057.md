---
title: 編譯器警告 (層級 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 234223ee7b6a031dd9e2c0fc88ccbbdba05beb3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622140"
---
# <a name="compiler-warning-level-4-c4057"></a>編譯器警告 (層級 4) C4057

'operator' : 'identifier1' 在間接取值上與 'identifier2' 的基底類型有些許不同

兩個指標運算式參考不同的基底類型。 運算式使用時沒有轉換。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 混合帶正負號和不帶正負號的類型。

1. 混合了 **short** 和 **long** 類型。