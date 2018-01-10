---
title: "hash 結構 (C++ 標準程式庫)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: thread/std::hash
dev_langs: C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7625249f9d602d9c23daa36d067059bbe66fba34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 **標頭：** \<執行緒 >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread>](../standard-library/thread.md)   
 [unary_function 結構](../standard-library/unary-function-struct.md)
