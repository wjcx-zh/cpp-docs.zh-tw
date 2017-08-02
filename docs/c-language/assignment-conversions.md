---
title: "指派轉換 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 44b9b5ede24d3b6e44813de46e7507f5d943a78f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="assignment-conversions"></a>指派轉換
在指派運算中，將指派值的類型會轉換成接收指派的變數類型。 C 可藉由指派而在整數和浮點類型之間轉換，即使資訊會在轉換過程中遺失。 使用的轉換方法取決於指派時採用的類型，如[一般算術轉換](../c-language/usual-arithmetic-conversions.md)與以下各節中所述：  
  
-   [從帶正負號整數型別的轉換](../c-language/conversions-from-signed-integral-types.md)  
  
-   [從不帶正負號整數型別的轉換](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [從浮點類型的轉換](../c-language/conversions-from-floating-point-types.md)  
  
-   [指標類型的轉換](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [從其他類型轉換](../c-language/conversions-from-other-types.md)  
  
 類型限定詞不會影響轉換的允許值，雖然 **const** 左值不可以在指派的左邊使用。  
  
## <a name="see-also"></a>另請參閱  
 [類型轉換](../c-language/type-conversions-c.md)
