---
title: NMAKE 嚴重錯誤 U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193260"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 嚴重錯誤 U1100

在批次規則 ' rule ' 的內容中，宏 ' macroname ' 不合法

當批次模式規則的命令區塊直接或間接參考非 $ < 的特殊檔案宏時，NMAKE 就會產生此錯誤。

$ < 是批次模式規則唯一允許的宏。
