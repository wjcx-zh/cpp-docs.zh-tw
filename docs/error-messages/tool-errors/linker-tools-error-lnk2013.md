---
title: 連結器工具錯誤 LNK2013 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9320b9ead0276b6fb5e1b9773260049a01520e12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2013"></a>連結器工具錯誤 LNK2013
修復類型修復溢位。 目標 'symbol name' 超出範圍  
  
 連結器無法容納所需的位址或位移指定的指令，所以目標符號太遠從指示的位置。  
  
 您可以解決這個問題，藉由建立多個映像，或使用[/](../../build/reference/order-put-functions-in-order.md)選項使指令與目標更接近。  
  
 符號名稱的使用者定義符號 （且不是編譯器產生的符號） 時，您也可以嘗試下列動作以解決此錯誤：  
  
-   變更為非靜態的靜態函數。  
  
-   重新命名包含靜態函式與呼叫端相同的程式碼區段。  
  
 使用`DUMPBIN /SYMBOLS`、 函式是否為靜態。