---
title: NMAKE 嚴重錯誤 U1051 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 570c7e5d8e6e8250a67e4f032ac26b04388cfd00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 嚴重錯誤 U1051
記憶體不足  
  
 NMAKE 已用盡記憶體，包括虛擬記憶體 makefile 因為太大或太複雜。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  釋放一些磁碟空間。  
  
2.  增加 Windows NT 分頁檔或 Windows 分頁檔的大小。  
  
3.  如果只使用 makefile 的一部分，請將 makefile 分割成不同的檔案或使用**！如果**前置處理器指示詞來限制所 NMAKE 必須處理的數量。 **！如果**指示詞包含**！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！其他** `IFDEF`，和**！其他** `IFNDEF`。