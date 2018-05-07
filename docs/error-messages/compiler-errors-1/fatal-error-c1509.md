---
title: 嚴重錯誤 C1509 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1509"></a>嚴重錯誤 C1509
編譯器限制： 函式 'function' 中的例外狀況處理常式狀態太多。 請簡化函式  
  
 程式碼超過內部限制在例外狀況處理常式狀態 （32768 狀態）。  
  
 最常見的原因是函式包含使用者定義的類別變數和算術運算子的複雜運算式。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  將通用子運算式指派給暫存變數來簡化運算式。  
  
2.  函式分割成較小的函式。