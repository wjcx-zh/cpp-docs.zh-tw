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
ms.openlocfilehash: 792c81e36b99bbac6c0417f0230bb1ea2bb1787c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200
讀取程式資料庫 'filename' 時發生錯誤  
  
 無法讀取程式資料庫 (PDB)。  
  
 這個錯誤可能被因檔案損毀。  
  
 如果`filename`是 PDB 檔，重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
 如果`filename`PDB 的主要輸出檔，並累加連結期間發生此錯誤，刪除 PDB 和重新連結。