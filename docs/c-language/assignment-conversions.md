---
title: "指派轉換 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e51b6af4006ad3d8b35f9167e4db4e3ea84a89f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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