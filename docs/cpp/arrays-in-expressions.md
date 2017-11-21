---
title: "運算式中的陣列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6f4bceac05f72c609c7aef8702c6313572ed6db5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="arrays-in-expressions"></a>運算式中的陣列
當陣列型別的識別項會出現在運算式中以外`sizeof`，傳址 (**&**)，或初始化的參考，它會轉換成第一個陣列元素的指標。 例如:   
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 指標 `psz` 會指向陣列 `szError1` 的第一個元素。 請注意，陣列 (和指標不同) 不是可修改的左值。 因此，下列指派是不合法的：  
  
```  
szError1 = psz;  
```  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../cpp/arrays-cpp.md)