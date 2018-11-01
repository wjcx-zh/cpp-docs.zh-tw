---
title: NMAKE 嚴重錯誤 U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: a1474acab4ca4929fb4db4b7b78d7a96637a0745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666592"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 嚴重錯誤 U1100

巨集 'macroname' 是在批次規則 'rule' 的內容中不合法

當批次模式規則的命令區塊直接或間接參考不是 $< 的特殊檔案巨集時，NMAKE 就會產生此錯誤。

$< 是批次模式規則中唯一允許的巨集。