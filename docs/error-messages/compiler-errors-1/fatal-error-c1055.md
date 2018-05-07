---
title: 嚴重錯誤 C1055 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07f0dc0e8dca08e8b0de47b73516d3fdfa21435b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1055"></a>嚴重錯誤 C1055
編譯器限制： 索引鍵不足  
  
 來源檔案包含太多符號。 編譯器已用完符號表的雜湊索引鍵。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  將來源檔案分割成較小的檔案。  
  
2.  消除不必要的標頭檔。  
  
3.  重複使用暫存和全域變數，而不必建立新的。