---
title: "字元化運算子 (#@) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6521322e7a71d8e76b657fb8580157c036e881b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="charizing-operator-"></a>字元化運算子 (#@)
**Microsoft 特定的**  
  
 字元化運算子只能搭配巨集的引數使用。 如果 **#@** 出現在型式參數之前在巨集的定義，實質引數是以單引號括住，而巨集展開時視為字元。 例如:   
  
```  
#define makechar(x)  #@x  
```  
  
 會使陳述式  
  
```  
a = makechar(b);  
```  
  
 展開成  
  
```  
a = 'b';  
```  
  
 單一引號字元不能與字元化運算子搭配使用。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)