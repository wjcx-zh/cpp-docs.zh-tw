---
title: "future_error 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_error
dev_langs:
- C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 07d01d2efc3aadf1d8b5a585b7f4c7b8b76d87cc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

---
# <a name="futureerror-class"></a>future_error 類別
描述可由管理 [future](../standard-library/future-class.md) 物件之類型的方法擲回的例外狀況物件。  
  
## <a name="syntax"></a>語法  
  
```
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \<未來 >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [logic_error 類別](../standard-library/logic-error-class.md)   
 [error_code 類別](../standard-library/error-code-class.md)

