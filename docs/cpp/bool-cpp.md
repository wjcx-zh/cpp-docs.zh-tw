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
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 564d2f4849d1725d46d92562e2ce75b2ea2e2d44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)