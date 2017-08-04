---
title: "主要運算式中的字串常值 | Microsoft Docs"
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
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
caps.latest.revision: 8
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
ms.openlocfilehash: baa7cc13f09b674f614b601690bac682b5f33013
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="string-literals-in-primary-expressions"></a>主要運算式中的字串常值
「字串常值」是以雙引號括住的字元、寬字元或一連串相鄰的字元。 由於字串常值不是變數，因此它們本身及擁有的任何項目都不可以是指派運算式的左運算元。 字串常值的類型為 `char` 陣列 (若為寬字串常值則為 `wchar_t` 陣列)。 運算式中的陣列會轉換成指標。 如需字串的詳細資訊，請參閱[字串常值](../c-language/c-string-literals.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C 主要運算式](../c-language/c-primary-expressions.md)
