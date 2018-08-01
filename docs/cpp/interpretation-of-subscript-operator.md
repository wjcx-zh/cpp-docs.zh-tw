---
title: 註標運算子的解譯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75659730198e09a172625c54bfcbdd54b7a9f857
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404784"
---
# <a name="interpretation-of-subscript-operator"></a>註標運算子的解譯
像其他運算子，註標運算子 (**[]**) 可以由使用者重新定義。 註標運算子的預設行為 (如果未多載) 是使用下列方法結合陣列名稱和註標：  
  
 \*((*subscript*) + (*註標*))  
  
 在包含指標類型的所有加法運算中，都會自動執行縮放來調整類型的大小。 因此，結果值不*下標*原點的位元組*陣列名稱*; 相反地，它是*註標*個元素的陣列。 (如需有關這項轉換的詳細資訊，請參閱 <<c0> [ 加法類運算子](../cpp/additive-operators-plus-and.md)。)  
  
 同樣地，對於多維陣列而言，位址是使用下列方法衍生：  
  
 **((**   
 ***陣列名稱*) + （**   
 ***註標*1***max*2  *\* max*3 *....max*n) **+** *下標*2  *\* max*3 *....max*n)。   。 。 *+* *註標*n))  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../cpp/arrays-cpp.md)