---
title: "NMAKE 警告 U4011 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ae15a3912fe3172e9dec98e1a90a3a262c47117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011
'target': 使用; 並非所有的相依性未建置目標  
  
 指定目標的相依性不存在或已過期，並更新相依項的命令傳回非零結束代碼。 [/K] 選項告訴 NMAKE 繼續處理不相關的組件的組建，並發出結束代碼為 1，NMAKE 工作階段完成時。  
  
 這項警告加上警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)無法建立或更新每個相依。