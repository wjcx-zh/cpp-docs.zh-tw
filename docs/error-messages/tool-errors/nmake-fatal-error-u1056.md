---
title: NMAKE 嚴重錯誤 U1056 |Microsoft 文件
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
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 嚴重錯誤 U1056
找不到命令處理器  
  
 中指定的路徑不是命令處理器**COMSPEC**或**路徑**環境變數。  
  
 NMAKE 使用 COMMAND.COM 或 CMD.以命令處理器執行命令時執行。 它會尋找命令處理器先在設定的路徑**COMSPEC**。 如果**COMSPEC**不存在，NMAKE 搜尋中指定的目錄**路徑**。