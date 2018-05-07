---
title: 連結器工具錯誤 LNK1200 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab32939c55dce5e27f907f3d23e639b24741cdc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200
讀取程式資料庫 'filename' 時發生錯誤  
  
 無法讀取程式資料庫 (PDB)。  
  
 這個錯誤可能被因檔案損毀。  
  
 如果`filename`是 PDB 檔，重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
 如果`filename`PDB 的主要輸出檔，並累加連結期間發生此錯誤，刪除 PDB 和重新連結。