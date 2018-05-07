---
title: NMAKE 警告 U4004 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 532abf2f62616d6e748c9a4e34f5c983f0853276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004
目標 'targetname' 有太多規則  
  
 使用單一的冒號，為給定的目標指定了多個描述區塊 (**:**) 做為分隔符號。 NMAKE 第一個描述區塊中執行命令並忽略後面的區塊。  
  
 若要指定相同的目標在多個相依性，使用雙冒號 (`::`) 為每個相依性行分隔符號。