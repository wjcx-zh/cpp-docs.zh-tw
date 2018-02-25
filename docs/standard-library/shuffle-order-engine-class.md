---
title: "shuffle_order_engine 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5916ace0b29ae29beb05448e493e90d9f7df877
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine 類別
透過重新排列基底引擎傳回的值產生隨機序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### <a name="parameters"></a>參數  
 `Engine`  
 基底引擎類型。  
  
 `K`  
 **資料表大小**。 緩衝區 (資料表) 中的項目數。 **前置條件**：`0 < K`  
  
## <a name="members"></a>成員  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 此範例類別描述「引擎配接器」，會透過重新排列其基底引擎所傳回的值來產生值。 每個建構函式會將內部資料表填入基底引擎傳回的 `K` 值，並在要求值時，從資料表選取隨機項目。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [\<random>](../standard-library/random.md)

