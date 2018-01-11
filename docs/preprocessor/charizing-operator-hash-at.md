---
title: "字元化運算子 (#@) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#@'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 933e97732462b61919d9e5a1e73f2a72d26ea01b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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