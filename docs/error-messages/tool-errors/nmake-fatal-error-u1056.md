---
title: NMAKE 嚴重錯誤 U1056 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065688"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 嚴重錯誤 U1056

找不到命令處理器

中指定的路徑不是命令處理器**COMSPEC**或是**路徑**環境變數。

NMAKE 使用 COMMAND.COM 或 cmd。為執行命令時在命令處理器的 EXE。 它會尋找命令處理器先在設定的路徑**COMSPEC**。 如果**COMSPEC**不存在，在指定的目錄的 NMAKE 搜尋**路徑**。