---
title: "type_index 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e00ba54975dfac0439509e63606e9992d86c9522
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="typeindex-class"></a>type_index 類別
`type_index` 類別會將指標包裝到 [type_info Class](../cpp/type-info-class.md) 來協助這類物件的索引。  
  
class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };  
  
 建構函式會將 `ptr` 初始化為 `&tinfo`。  
  
 `name` 會傳回 `ptr->name()`。  
  
 `hash_code` 傳回 `ptr->hash_code().`  
  
 `operator==` 會傳回 `*ptr == right.ptr`。  
  
 `operator!=` 會傳回 `!(*this == right)`。  
  
 `operator<` 會傳回 `*ptr->before(*right.ptr)`。  
  
 `operator<=` 傳回 `!(right < *this).`  
  
 `operator>` 會傳回 `right < *this`。  
  
 `operator>=` 會傳回 `!(*this < right)`。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [\<typeindex>](../standard-library/typeindex.md)




