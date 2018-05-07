---
title: 運算式評估工具錯誤 CXX0017 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7540dc701ffa6e0acb3d2661e1196e5f4552d2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0017"></a>運算式評估工具錯誤 CXX0017
找不到符號  
  
 找不到運算式中指定的符號。  
  
 此錯誤的其中一個可能的原因是符號名稱的大小寫不符。 由於 C 和 c + + 會區分大小寫的語言，符號名稱必須是指定它定義在來源中的大小寫完全相符。  
  
 嘗試在偵錯期間監看變數類型轉換變數時，會發生此錯誤。 `typedef`宣告的型別，新名稱，但沒有定義新的類型。 試圖在偵錯工具需要有已定義的類型名稱。  
  
 這個錯誤是與 can0017 相同。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  請確定該符號已宣告其中正在使用的程式中的點。  
  
2.  使用實際的型別名稱，來轉換變數在偵錯工具，而非`typedef`-定義的名稱。