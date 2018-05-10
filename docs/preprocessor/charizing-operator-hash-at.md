---
title: 字元化運算子 (#@) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="charizing-operator-"></a>字元化運算子 (#@)
**Microsoft 專屬**  
  
 字元化運算子只能搭配巨集的引數使用。 如果**#@** 出現在型式參數之前在巨集的定義，實質引數是以單引號括住，而巨集展開時視為字元。 例如:   
  
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
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)