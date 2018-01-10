---
title: "嚴重錯誤 C1509 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1509
dev_langs: C++
helpviewer_keywords: C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22cb22ea2186b16fd98d2714779b2475c51d15bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1509"></a>嚴重錯誤 C1509
編譯器限制： 函式 'function' 中的例外狀況處理常式狀態太多。 請簡化函式  
  
 程式碼超過內部限制在例外狀況處理常式狀態 （32768 狀態）。  
  
 最常見的原因是函式包含使用者定義的類別變數和算術運算子的複雜運算式。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  將通用子運算式指派給暫存變數來簡化運算式。  
  
2.  函式分割成較小的函式。