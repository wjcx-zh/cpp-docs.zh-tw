---
title: NMAKE 嚴重錯誤 U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182899"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 嚴重錯誤 U1056

找不到命令處理器

命令處理器不在**COMSPEC**或**path**環境變數所指定的路徑中。

NMAKE 會使用 COMMAND.COM 或 CMD。執行命令時，EXE 做為命令處理器。 它會先在**COMSPEC**中設定的路徑中尋找命令處理器。 如果**COMSPEC**不存在，NMAKE 會搜尋**PATH**中指定的目錄。
