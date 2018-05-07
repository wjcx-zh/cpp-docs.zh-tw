---
title: 連結器工具錯誤 LNK1140 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc0d59589a1882aca4ef2deb419e1e4f1081e52b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1140"></a>連結器工具錯誤 LNK1140
程式資料庫的模組太多連結，以 /PDB: NONE  
  
 專案包含超過 4096 個模組。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  重新連結使用[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。  
  
2.  但不偵錯資訊編譯某些模組。  
  
3.  降低模組的數目。