---
title: "hash 結構 (C++ 標準程式庫)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 1af8dc2f8fef535883088c413827a98a35539980
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

---
# <a name="hash-structure-c-standard-library"></a>hash 結構 (C++ 標準程式庫)
定義傳回由 `Val` 唯一決定值的成員函式。 成員函式會定義 [hash](../standard-library/hash-class.md) 函式，適用於將 `thread::id` 類型的值對應到索引值的分佈。  
  
## <a name="syntax"></a>語法  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \<執行緒 >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread>](../standard-library/thread.md)   
 [unary_function 結構](../standard-library/unary-function-struct.md)

