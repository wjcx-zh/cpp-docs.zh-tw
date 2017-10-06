---
title: "註標運算子的解譯 |Microsoft 文件"
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
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
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
ms.openlocfilehash: 1a83ff6aea4380688d3b6298b93e04caab1dbb7f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="interpretation-of-subscript-operator"></a>註標運算子的解譯
就如同其他運算子，註標運算子一樣 (**[]**) 可以由使用者重新加以定義。 註標運算子的預設行為 (如果未多載) 是使用下列方法結合陣列名稱和註標：  
  
 \*((*陣列名稱*) + (*註標*))  
  
 在包含指標類型的所有加法運算中，都會自動執行縮放來調整類型的大小。 因此，結果值不*註標*的原始位元組*陣列名稱*; 相反地，它是*註標*個元素的陣列。 (如需有關這項轉換的詳細資訊，請參閱[加法類運算子](../cpp/additive-operators-plus-and.md)。)  
  
 同樣地，對於多維陣列而言，位址是使用下列方法衍生：  
  
 **((**   
 ***陣列名稱*) + （**   
 ***註標*1***max*2 * \* max*3*...max*n) ** + ***註標*2 * \* max*3*...max*n)。   。 。 *+**註標*n))  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../cpp/arrays-cpp.md)
