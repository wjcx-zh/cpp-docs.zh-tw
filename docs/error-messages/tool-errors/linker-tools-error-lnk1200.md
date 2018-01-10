---
title: "連結器工具錯誤 LNK1200 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1200
dev_langs: C++
helpviewer_keywords: LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70bf262d4f99c807e3488c1f9b2ed9e73b1eb715
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200
讀取程式資料庫 'filename' 時發生錯誤  
  
 無法讀取程式資料庫 (PDB)。  
  
 這個錯誤可能被因檔案損毀。  
  
 如果`filename`是 PDB 檔，重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
 如果`filename`PDB 的主要輸出檔，並累加連結期間發生此錯誤，刪除 PDB 和重新連結。