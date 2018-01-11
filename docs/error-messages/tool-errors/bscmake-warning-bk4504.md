---
title: "BSCMAKE 警告 BK4504 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK4504
dev_langs: C++
helpviewer_keywords: BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 58a59b3141a8d7051aa7ece1bcb71dd960fabb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504
檔案包含太多的參考。正在略過此來源的進一步參考  
  
 .cpp 檔包含 64,000 個以上的符號參考。 當 BSCMAKE 在檔案中遇到 64,000 個參考，會忽略所有進一步的參考。  
  
 若要修正這個問題，您可以將檔案分割成兩個以上的檔案，每一個有少於 64,000 個符號參考，或使用 `#pragma component(browser)` 前置處理器指示詞，限制為特定參考所產生的符號。 如需詳細資訊，請參閱[元件](../../preprocessor/component.md)。