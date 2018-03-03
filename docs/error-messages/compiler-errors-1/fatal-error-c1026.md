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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 206e9843fd8566f4f595a46918548af14f119439
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026
剖析器堆疊溢位，程式太複雜  
  
 剖析程式所需的空間會造成編譯器堆疊溢位。  
  
 減少複雜度的運算式：  
  
-   減少的巢狀`for`和`switch`陳述式。 更深的巢狀陳述式置於個別的函式中。  
  
-   中斷長涉及逗號運算子或函數呼叫的運算式。