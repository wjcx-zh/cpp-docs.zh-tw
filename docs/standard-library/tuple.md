---
title: '&lt;tuple&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <tuple>
dev_langs: C++
helpviewer_keywords: tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: df03116e230a9cba7721a37701e9b67ac8e8a518
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="lttuplegt"></a>&lt;tuple&gt;
定義樣板 `tuple`，其執行個體會保留各種不同類型的物件。  
  
## <a name="syntax"></a>語法  
  
```  
#include <tuple>  
```  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[tuple](../standard-library/tuple-class.md)|包裝固定長度的元素序列。|  
|[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)|包裝 `tuple` 元素的類型。|  
|[tuple_size 類別](../standard-library/tuple-size-class-tuple.md)|包裝 `tuple` 項目計數。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|比較 `tuple` 物件 (等於)|  
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比較 `tuple` 物件 (不等於)|  
|[operator<](../standard-library/tuple-operators.md#op_lt)|比較 `tuple` 物件 (小於)|  
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|比較 `tuple` 物件 (小於或等於)|  
|[operator>](../standard-library/tuple-operators.md#op_gt)|比較 `tuple` 物件 (大於)|  
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|比較 `tuple` 物件 (大於或等於)|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[get](../standard-library/tuple-functions.md#get)|從 `tuple` 物件取得項目。|  
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|從元素值製作 `tuple`。|  
|[tie](../standard-library/tuple-functions.md#tie)|從元素參考製作 `tuple`。|  
  
## <a name="see-also"></a>另請參閱  
 [\<array>](../standard-library/array.md)

