---
title: "NMAKE 嚴重錯誤 U1051 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93c109bf723b3c4cf08e998a715fe8f6f33be466
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 嚴重錯誤 U1051
記憶體不足  
  
 NMAKE 已用盡記憶體，包括虛擬記憶體 makefile 因為太大或太複雜。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  釋放一些磁碟空間。  
  
2.  增加 Windows NT 分頁檔或 Windows 分頁檔的大小。  
  
3.  如果只使用 makefile 的一部分，請將 makefile 分割成不同的檔案或使用**！如果**前置處理器指示詞來限制所 NMAKE 必須處理的數量。 **！如果**指示詞包含**！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！其他** `IFDEF`，和**！其他** `IFNDEF`。