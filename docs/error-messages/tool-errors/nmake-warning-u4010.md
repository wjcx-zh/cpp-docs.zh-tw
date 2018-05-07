---
title: NMAKE 警告 U4010 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8c99bb4a9b5daf7f630771d0f240479aaf5f3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010
'target': 建置失敗;/K 指定，繼續進行...  
  
 給定的目標的命令區塊中的命令傳回非零結束代碼。 [/K] 選項告訴 NMAKE 繼續處理不相關的組件的組建，並發出結束代碼為 1，NMAKE 工作階段完成時。  
  
 如果給定的目標是本身，另一個目標相依，NMAKE 就會發出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)之後這個警告。