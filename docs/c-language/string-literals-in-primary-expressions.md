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
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: d1ed5731f0b46769ac9f49c34752d8794a0dddc8
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="string-literals-in-primary-expressions"></a>主要運算式中的字串常值
「字串常值」是以雙引號括住的字元、寬字元或一連串相鄰的字元。 由於字串常值不是變數，因此它們本身及擁有的任何項目都不可以是指派運算式的左運算元。 字串常值的類型為 `char` 陣列 (若為寬字串常值則為 `wchar_t` 陣列)。 運算式中的陣列會轉換成指標。 如需字串的詳細資訊，請參閱[字串常值](../c-language/c-string-literals.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C 主要運算式](../c-language/c-primary-expressions.md)
