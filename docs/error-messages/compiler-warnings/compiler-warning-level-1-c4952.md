---
title: 編譯器警告 （層級 1） C4952 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42696dfae816742c958bca23e25e311e834dd62a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4952"></a>編譯器警告 (層級 1) C4952
'function' : 在程式資料庫 'pgd_file' 中找不到分析資料  
  
 使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到輸入模組在 `/LTCG:PGINSTRUMENT` 之後經過重新編譯，且出現新的函式 ()。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。