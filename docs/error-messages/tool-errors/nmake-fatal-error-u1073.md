---
title: NMAKE 嚴重錯誤 U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366924"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 嚴重錯誤 U1073

不知道如何進行 'targetname'

指定的目標不存在，並沒有任何要執行的命令或套用推斷規則。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 檢查目標名稱的拼字。

1. 如果*targetname*是虛擬目標，其指定為目標，以在另一個描述區塊中。

1. 如果*targetname*是巨集引動過程中，確定它不會展開為 null 的字串。