---
title: "編譯器警告 （層級 3） C4622 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4622
dev_langs: C++
helpviewer_keywords: C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52f4491d26cfa56f48ed479b30daeafe9cc01adf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4622"></a>編譯器警告 (層級 3) C4622
覆寫在目的檔中建立先行編譯標頭檔期間產生的偵錯資訊: 'file'  
  
 所指定檔案中的 CodeView 資訊在使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (使用先行編譯標頭檔) 選項編譯時遺失。  
  
 建立或使用先行編譯標頭檔時，請重新命名物件檔案 (使用 [/Fo](../../build/reference/fo-object-file-name.md))，或者使用新的物件檔案進行連結。