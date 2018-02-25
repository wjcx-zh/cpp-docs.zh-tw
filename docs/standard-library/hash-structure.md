---
title: "hash 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- typeindex/std::hash
dev_langs:
- C++
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cce31fd8c401c7657ac8352ce41d68fe263d006f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="hash-structure"></a>hash 結構
樣板類別將它的方法定義為傳回 `val.hash_code()`。 方法會定義雜湊函式，用來將 [type_index](../standard-library/type-index-class.md) 類型的值對應到索引值的分佈。  
  
## <a name="syntax"></a>語法  
  
```
template <>
struct hash<type_index>  
: public unary_function<type_index, size_t>
 { // hashes a typeinfo object
    size_t operator()(type_index val) const;

 };
```  
  
## <a name="see-also"></a>請參閱  
 [\<typeindex>](../standard-library/typeindex.md)



