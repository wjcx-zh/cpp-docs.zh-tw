---
title: 嚴重錯誤 C1026 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c034d45b7f8b222471094f4580902ae1b8dc66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198101"
---
# <a name="fatal-error-c1026"></a>嚴重錯誤 C1026
剖析器堆疊溢位，程式太複雜  
  
 剖析程式所需的空間會造成編譯器堆疊溢位。  
  
 減少複雜度的運算式：  
  
-   減少的巢狀`for`和`switch`陳述式。 更深的巢狀陳述式置於個別的函式中。  
  
-   中斷長涉及逗號運算子或函數呼叫的運算式。