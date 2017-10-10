---
title: "嚴重錯誤 C1026 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 187cfc1a59fc40a721be09aef9e78ef36c68f66a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026
剖析器堆疊溢位，程式太複雜  
  
 剖析程式所需的空間會造成編譯器堆疊溢位。  
  
 減少複雜度的運算式：  
  
-   減少的巢狀`for`和`switch`陳述式。 更深的巢狀陳述式置於個別的函式中。  
  
-   中斷長涉及逗號運算子或函數呼叫的運算式。
