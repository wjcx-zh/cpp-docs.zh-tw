---
title: "hash 結構 (STL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "thread/std::hash"
dev_langs: 
  - "C++"
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# hash 結構 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義成員函式的傳回值，唯一取決於 `Val`。 成員函式定義 [雜湊](../standard-library/hash-class.md) 適用於類型的對應值的函式 `thread::id` 索引值的分佈。  
  
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
 **標頭︰** 執行緒  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\< 執行緒>](../standard-library/thread.md)   
 [unary_function 結構](../standard-library/unary-function-struct.md)
