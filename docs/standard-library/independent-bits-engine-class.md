---
title: "independent_bits_engine 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2f5b064b91aa6df766ff4ca460a6096f984ab8b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="independentbitsengine-class"></a>independent_bits_engine 類別
重新封裝基底引擎所傳回值的位元，以產生具有指定位元數的隨機一連串數字。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>參數  
 `Engine`  
 基底引擎類型。  
  
 `W`  
 **字組大小**。 每個所產生數字的大小 (位元)。 **前置條件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="members"></a>成員  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 此範本類別描述一個「引擎配接器」(engine adaptor)*`W`，此配接器會將來自其基底引擎所傳回值的位元重新封裝來產生值，而導致產生*  位元值。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [\<random>](../standard-library/random.md)

