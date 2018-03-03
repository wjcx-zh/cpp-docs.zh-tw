---
title: "連結器工具錯誤 LNK1140 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5a7bce157359d547f91ba2b560cf258e231b4a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1140"></a>連結器工具錯誤 LNK1140
程式資料庫的模組太多連結，以 /PDB: NONE  
  
 專案包含超過 4096 個模組。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  重新連結使用[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。  
  
2.  但不偵錯資訊編譯某些模組。  
  
3.  降低模組的數目。