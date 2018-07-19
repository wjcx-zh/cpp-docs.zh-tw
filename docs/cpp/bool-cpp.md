---
title: bool （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3bd43c9ceb4f0a0f73b86e3a4ecf4d851d504b3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939308"
---
# <a name="bool-c"></a>bool (C++)

這個關鍵字是內建類型。 此類型的變數可以有值[，則為 true](../cpp/true-cpp.md)並[false](../cpp/false-cpp.md)。 條件運算式具有類型**bool** ，因此有值的型別**bool**。 例如，`i!=0`現在有 為 TRUE 或 FALSE 的值而定`i`。  

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 運算元的後置或前置詞遞增或遞減運算子可能不是類型**bool**。 換句話說，指定變數`b`型別的**bool**，不再允許這些運算式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
TRUE 和 FALSE 的值具有下列關聯性：  
  
```cpp  
!false == true  
!true == false  
```  
  
在下列陳述式中：  
  
```cpp  
if (condexpr1) statement1;   
```  
  
如果`condexpr1`為 TRUE 時，`statement1`一定會執行，如果`condexpr1`為 FALSE，`statement1`永遠不會執行。  
  
當置或後置**++** 運算子會套用至型別的變數**bool**，變數會設為 TRUE。 
**Visual Studio 2017 版本 15.3 和更新版本**： 的 operator + + **bool**已移除的語言並不受支援。

後置或前置詞**--** 無法將運算子套用至這個類型的變數。  
  
 **Bool**類型會參與整數提升。 類型的右值**bool**可以轉換成的型別**int**、 與 FALSE 成為零，變成一，則為 TRUE。 做為不同的類型， **bool**參與多載解析。  
  
## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[基本類型](../cpp/fundamental-types-cpp.md)<br/>
