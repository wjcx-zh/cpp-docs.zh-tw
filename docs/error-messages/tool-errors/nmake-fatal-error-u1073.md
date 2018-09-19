---
title: NMAKE 嚴重錯誤 U1073 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c309ed94cd1c984406e0d21f0139e35c6e41d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053932"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 嚴重錯誤 U1073

不知道如何進行 'targetname'

指定的目標不存在，並沒有任何要執行的命令或套用推斷規則。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 檢查目標名稱的拼字。

1. 如果*targetname*是虛擬目標，其指定為目標，以在另一個描述區塊中。

1. 如果*targetname*是巨集引動過程中，確定它不會展開為 null 的字串。