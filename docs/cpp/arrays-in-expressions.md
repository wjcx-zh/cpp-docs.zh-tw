---
title: "運算式中的陣列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ec97fba837ffae0a03ff8d4fc3d85c4011aa59c6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
