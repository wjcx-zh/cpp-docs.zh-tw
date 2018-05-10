---
title: 主要運算式中的字串常值 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5fd8c73bb9dac5a26c62b86bdc4038bd26a0829
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="string-literals-in-primary-expressions"></a>主要運算式中的字串常值
「字串常值」是以雙引號括住的字元、寬字元或一連串相鄰的字元。 由於字串常值不是變數，因此它們本身及擁有的任何項目都不可以是指派運算式的左運算元。 字串常值的類型為 `char` 陣列 (若為寬字串常值則為 `wchar_t` 陣列)。 運算式中的陣列會轉換成指標。 如需字串的詳細資訊，請參閱[字串常值](../c-language/c-string-literals.md)。  
  
## <a name="see-also"></a>請參閱  
 [C 主要運算式](../c-language/c-primary-expressions.md)