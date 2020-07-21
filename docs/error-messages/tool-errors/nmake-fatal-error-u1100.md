---
title: NMAKE 嚴重錯誤 U1100
description: Microsoft NMAKE 嚴重錯誤 U1100 的原因描述。
ms.date: 07/17/2020
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: f908514469a6c9fdb53df3b2bded1b30bddc5a41
ms.sourcegitcommit: 00af3df3331854b23693ee844e5e7c10c8b05a90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86491384"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 嚴重錯誤 U1100

> 在批次規則 '*rule-name*' 的內容中，宏 '*宏名稱*' 不合法

當批次模式規則的命令區塊直接或間接參考不是的特殊檔案宏時，NMAKE 就會產生此錯誤 `$<` 。

`$<`是批次模式規則唯一允許的宏。

如需批次規則中 NMAKE 宏的詳細資訊，請參閱[特殊的 nmake 宏](../../build/reference/special-nmake-macros.md)。
