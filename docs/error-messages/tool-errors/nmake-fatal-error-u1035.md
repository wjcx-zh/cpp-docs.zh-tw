---
title: NMAKE 嚴重錯誤 U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193715"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 嚴重錯誤 U1035

語法錯誤：必須是 '： ' 或 ' = ' 分隔符號

必須是冒號（ **：** ）或等號（ **=** ）。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 不是在目標後面的冒號。

1. 冒號且不含空格（例如：）後面接著單一字母目標。 NMAKE 將它解釋為磁片磁碟機規格。

1. 推斷規則未遵循冒號。

1. 巨集定義後面沒有等號。

1. 後面接著一個字元，用來將命令繼續到新行的反斜線（ **\\** ）。

1. 出現未遵循任何 NMAKE 語法規則的字串。

1. Makefile 已由字處理器格式化。
