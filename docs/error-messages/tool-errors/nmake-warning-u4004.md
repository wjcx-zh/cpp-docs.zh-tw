---
title: "NMAKE 警告 U4004 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcbda9dd9d7ca5ecb99e46b9916fb95c2c560e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004
目標 'targetname' 有太多規則  
  
 使用單一的冒號，為給定的目標指定了多個描述區塊 (**:**) 做為分隔符號。 NMAKE 第一個描述區塊中執行命令並忽略後面的區塊。  
  
 若要指定相同的目標在多個相依性，使用雙冒號 (`::`) 為每個相依性行分隔符號。