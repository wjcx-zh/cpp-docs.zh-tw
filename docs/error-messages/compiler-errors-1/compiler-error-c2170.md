---
title: 編譯器錯誤 C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445691"
---
# <a name="compiler-error-c2170"></a>編譯器錯誤 C2170

'identifier': 未宣告為函式，不可為內建函式

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Pragma`intrinsic`用於函式以外的項目。

1. Pragma`intrinsic`用於沒有任何內建形式的函式。