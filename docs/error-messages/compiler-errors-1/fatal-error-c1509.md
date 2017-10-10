---
title: "嚴重錯誤 C1509 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3d3fc7a7be867a7137dab4155984cf1844b661ea
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1509"></a>嚴重錯誤 C1509
編譯器限制： 函式 'function' 中的例外狀況處理常式狀態太多。 請簡化函式  
  
 程式碼超過內部限制在例外狀況處理常式狀態 （32768 狀態）。  
  
 最常見的原因是函式包含使用者定義的類別變數和算術運算子的複雜運算式。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  將通用子運算式指派給暫存變數來簡化運算式。  
  
2.  函式分割成較小的函式。
