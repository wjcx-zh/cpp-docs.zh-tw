---
title: NMAKE 警告 U4011 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9c0f90c507eebe212a9c3cbfb2f2d21cded43d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011
'target': 使用; 並非所有的相依性未建置目標  
  
 指定目標的相依性不存在或已過期，並更新相依項的命令傳回非零結束代碼。 [/K] 選項告訴 NMAKE 繼續處理不相關的組件的組建，並發出結束代碼為 1，NMAKE 工作階段完成時。  
  
 這項警告加上警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)無法建立或更新每個相依。