---
title: 主要運算式中的識別項 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9f39f7ce609ea06a2d991ac79c2b1151625bc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="identifiers-in-primary-expressions"></a>主要運算式中的識別項
識別項可能包括整數、**浮點數**、`enum`、`struct`、**等位**、陣列、指標或函式類型。 識別項是主要運算式，但前提是已經宣告為指定物件 (此時為左值) 或函式 (此時為函式指示項)。 如需左值的定義，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。  
  
 陣列識別項所代表的指標值並不是變數，因此陣列識別項無法構成指派作業的左運算元，因此不是可修改的左值。  
  
 宣告為函式的識別項代表指標，其值即為該函式的位址。 該指標會設定傳回指定類型之函式的位址。 因此，函式識別項也不能是指派作業的左值。 如需詳細資訊，請參閱[識別項](../c-language/c-identifiers.md)。  
  
## <a name="see-also"></a>請參閱  
 [C 主要運算式](../c-language/c-primary-expressions.md)