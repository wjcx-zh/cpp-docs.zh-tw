---
title: BSCMAKE 警告 BK4504 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a17aa8b4e2a98d3bda5d21ea84962791b8051dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504
檔案包含太多的參考。正在略過此來源的進一步參考  
  
 .cpp 檔包含 64,000 個以上的符號參考。 當 BSCMAKE 在檔案中遇到 64,000 個參考，會忽略所有進一步的參考。  
  
 若要修正這個問題，您可以將檔案分割成兩個以上的檔案，每一個有少於 64,000 個符號參考，或使用 `#pragma component(browser)` 前置處理器指示詞，限制為特定參考所產生的符號。 如需詳細資訊，請參閱[元件](../../preprocessor/component.md)。