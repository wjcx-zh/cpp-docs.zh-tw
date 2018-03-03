---
title: "NMAKE 警告 U4010 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2d90e95a3417241991eb01f0ec718d75cd8558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010
'target': 建置失敗;/K 指定，繼續進行...  
  
 給定的目標的命令區塊中的命令傳回非零結束代碼。 [/K] 選項告訴 NMAKE 繼續處理不相關的組件的組建，並發出結束代碼為 1，NMAKE 工作階段完成時。  
  
 如果給定的目標是本身，另一個目標相依，NMAKE 就會發出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)之後這個警告。