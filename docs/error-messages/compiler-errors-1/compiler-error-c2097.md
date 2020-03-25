---
title: 編譯器錯誤 C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: cdb14aeef61d136a6992a05a72f382e589e88770
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207490"
---
# <a name="compiler-error-c2097"></a>編譯器錯誤 C2097

不合法的初始化

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 使用非常數值來初始化變數。

1. 使用長位址初始化短位址。

1. 使用 **/za**進行編譯時，使用非常數運算式初始化本機結構、等位或陣列。

1. 使用包含逗號運算子的運算式進行初始化。

1. 使用既不是常數也不是符號的運算式進行初始化。
