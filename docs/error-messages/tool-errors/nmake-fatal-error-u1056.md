---
title: "NMAKE 嚴重錯誤 U1056 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1056
dev_langs: C++
helpviewer_keywords: U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41db646e2559051c11de5265900dde8ad0a03214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 嚴重錯誤 U1056
找不到命令處理器  
  
 中指定的路徑不是命令處理器**COMSPEC**或**路徑**環境變數。  
  
 NMAKE 使用 COMMAND.COM 或 CMD.以命令處理器執行命令時執行。 它會尋找命令處理器先在設定的路徑**COMSPEC**。 如果**COMSPEC**不存在，NMAKE 搜尋中指定的目錄**路徑**。