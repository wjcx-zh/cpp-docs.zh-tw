---
title: 編譯器警告 (層級 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: d0bae91af3c2bfed97e252a74232e2a1bd778347
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225289"
---
# <a name="compiler-warning-level-4-c4057"></a>編譯器警告 (層級 4) C4057

'operator' : 'identifier1' 在間接取值上與 'identifier2' 的基底類型有些許不同

兩個指標運算式參考不同的基底類型。 運算式使用時沒有轉換。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 混合帶正負號和不帶正負號的類型。

1. 混合 **`short`** 和 **`long`** 類型。
