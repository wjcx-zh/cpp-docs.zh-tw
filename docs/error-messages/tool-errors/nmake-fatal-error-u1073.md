---
title: NMAKE 嚴重錯誤 U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182691"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 嚴重錯誤 U1073

不知道如何建立「targetname」

指定的目標不存在，而且沒有可執行檔命令或要套用的推斷規則。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 檢查目標名稱的拼寫。

1. 如果*targetname*是偽目標，請將它指定為另一個描述區塊中的目標。

1. 如果*targetname*是宏調用，請確定它不會展開為 null 字串。
