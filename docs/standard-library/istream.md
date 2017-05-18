---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::<istream>
- std.<istream>
- <istream>
- std::<istream>
dev_langs:
- C++
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a329d340709ca5d74f6a52c6ee6c8070ef2faa7f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltistreamgt"></a>&lt;istream&gt;
定義範本類別 basic_istream，以調解 iostreams 的擷取，並定義範本類別 basic_iostream，以調解插入和擷取。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。  
  
## <a name="syntax"></a>語法  
  
```  
#include <istream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[iostream](../standard-library/istream-typedefs.md#iostream)|`char` 的特殊化類型 `basic_iostream`。|  
|[istream](../standard-library/istream-typedefs.md#istream)|`char` 的特殊化類型 `basic_istream`。|  
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|針對 **wchar** 特殊化的 `basic_iostream` 類型。|  
|[wistream](../standard-library/istream-typedefs.md#wistream)|針對 **wchar** 特殊化的 `basic_istream` 類型。|  
  
### <a name="manipulators"></a>操作工具  
  
|||  
|-|-|  
|[ws](../standard-library/istream-functions.md#ws)|略過資料流中的空白字元。|  
|[swap](../standard-library/istream-functions.md#istream_swap)|交換兩個資料流物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|從資料流中擷取字元和字串。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[basic_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|  
|[basic_istream](../standard-library/basic-istream-class.md)|此範本類別描述一個物件，此物件可控制如何從具有 **Elem** 類型 (也稱為 [char_type](../standard-library/basic-ios-class.md#char_type)) 之元素的資料流緩衝區擷取元素和編碼物件，其中該類型的字元特性是由 **Tr** 類別 (也稱為 [traits_type](../standard-library/basic-ios-class.md#traits_type)) 所決定。|  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)




