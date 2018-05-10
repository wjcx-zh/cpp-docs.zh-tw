---
title: 屬性內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e220eb0e7eb80d01d70aed82e773c46fe6704c7d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="attribute-contexts"></a>屬性內容
C + + 屬性可以使用四個基本的欄位描述： 將它們套用至目標 (**套用至**) 或不屬於可重複，(**Repeatable**)、 所需的其他屬性 (存在**必要屬性**)，並與其他屬性的不相容 (**屬性無效**)。 在每個屬性的參考主題中的表格會列出這些欄位。 下面會描述每一個欄位。  
  
## <a name="applies-to"></a>適用於  
 此欄位描述的不同 c + + 語言項目所指定之屬性的合法目標。 比方說，如果屬性指定 「 類別 」 中**套用至**欄位，這會指出屬性只能套用至合法的 c + + 類別。 如果屬性套用至類別的成員函式，會產生語法錯誤。  
  
 如需詳細資訊，請參閱[屬性的用法](../windows/attributes-by-usage.md)。  
  
## <a name="repeatable"></a>可重複  
 此欄位會指出是否屬性可以重複套用至相同的目標。 大部分的屬性不是可重複的。  
  
## <a name="required-attributes"></a>必要屬性  
 此欄位會列出其他需要的屬性才能正確執行指定的屬性存在 （亦即，套用至相同的目標）。 這很有任何項目，這個欄位的屬性。  
  
## <a name="invalid-attributes"></a>無效的屬性  
 此欄位會列出與指定的屬性不相容的其他屬性。 這很有任何項目，這個欄位的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 屬性參考](../windows/cpp-attributes-reference.md)