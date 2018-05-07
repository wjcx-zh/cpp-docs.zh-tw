---
title: 嚴重錯誤 C1002 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1002"></a>嚴重錯誤 C1002
編譯器於第二編譯階段堆積空間不足  
  
 在其第二個階段，可能是因為太多符號或複雜運算式的程式編譯器動態記憶體空間不足。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  將來源檔案分割成幾個較小的檔案。  
  
2.  分成較小的子運算式的運算式。  
  
3.  其他程式或消耗記憶體的驅動程式移除。