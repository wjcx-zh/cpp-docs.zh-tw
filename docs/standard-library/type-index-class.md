---
title: "type_index 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "typeindex/std::type_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "type_index 類別"
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# type_index 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`type_index` 類別會封裝指標 [type\_info 類別](../cpp/type-info-class.md) 協助索引由這類物件。  
  
```  
class type_index {  
public:  
    type_index(const type_info& tinfo);  
    const char *name() const;  
    size_t hash_code() const;  
    bool operator==(const type_info& right) const;  
    bool operator!=(const type_info& right) const;  
    bool operator<(const type_info& right) const;  
    bool operator<=(const type_info& right) const;  
    bool operator>(const type_info& right) const;  
    bool operator>=(const type_info& right) const;  
};  
```  
  
 建構函式會將 `ptr` 設定為 `&tinfo`。  
  
 `name` 傳回 `ptr->name()`。  
  
 `hash_code` 會傳回 `ptr->hash_code().`  
  
 `operator==` 傳回 `*ptr == right.ptr`。  
  
 `operator!=` 傳回 `!(*this == right)`。  
  
 `operator<` 傳回 `*ptr->before(*right.ptr)`。  
  
 `operator<=` 會傳回 `!(right < *this).`  
  
 `operator>`的會傳回 `right < *this`。  
  
 `operator>=` 傳回 `!(*this < right)`。  
  
## 請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [\<typeindex\>](../standard-library/typeindex.md)