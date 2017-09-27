---
title: "bool （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bool_cpp
- bool
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 9
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
ms.openlocfilehash: f2437d831ae155f916b69cc6b35d3b586be9819e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="bool-c"></a>bool (C++)
這個關鍵字是內建類型。 此類型的變數可以有值[true](../cpp/true-cpp.md)和[false](../cpp/false-cpp.md)。 條件運算式具有 `bool` 類型，因此具有 `bool` 類型的值。 例如，`i!=0`現在具有**true**或**false**的值而定`i`。  

**Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 運算元置或後置遞增或遞減運算子可能不是型別`bool`。 
  
 值**true**和**false**具有下列關聯性：  
  
```  
!false == true  
!true == false  
```  
  
 在下列陳述式中：  
  
```  
if (condexpr1) statement1;   
```  
  
 如果`condexpr1`是**true**，`statement1`一定會執行，如果`condexpr1`是**false**，`statement1`永遠不會執行。  
  
 後置或前置詞時`++`運算子會套用至類型的變數`bool`，此變數設為**true**。 
**Visual Studio 2017 15.3 和更新版本**: operator + + 的 bool 已移除的語言，並已不再支援。

後置或前置 `--` 運算子不可套用至這種類型的變數。  
  
 `bool` 類型會參與整數提升。 類型的右`bool`可以轉換成類型的右`int`，與**false**變成零和**true**變成一。 `bool` 為不同類型，它會參與多載解析。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)
