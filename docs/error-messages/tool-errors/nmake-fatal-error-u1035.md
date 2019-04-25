---
title: NMAKE 嚴重錯誤 U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324333"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 嚴重錯誤 U1035

語法錯誤： 必須是 ':' 或 '=' 分隔符號

冒號 (**:**) 或等號 (**=**) 所預期。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 冒號未遵循為目標。

1. 冒號且不得包含空格 （例如，a:） 後面接著單一字母的目標。 NMAKE 解譯它做為磁碟機規格。

1. 冒號未遵循推斷規則。

1. 巨集定義後面沒有等號。

1. 字元後面接著反斜線 (**\\**)，用來繼續執行至新的一行命令。

1. 在出現未遵循任何 NMAKE 語法規則的字串。

1. 文書處理器來格式化的 makefile。