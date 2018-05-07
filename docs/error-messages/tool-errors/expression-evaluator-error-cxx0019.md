---
title: 運算式評估工具錯誤 CXX0019 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0019"></a>運算式評估工具錯誤 CXX0019
不正確的類型轉換  
  
 C 運算式評估工具無法執行轉換所寫的類型。  
  
 這個錯誤是與 can0019 相同。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  指定的類型為 unknown。  
  
2.  沒有太多層指標類型。 例如，類型轉換  
  
    ```  
    (char **)h_message  
    ```  
  
     無法評估由 C 運算式評估工具。