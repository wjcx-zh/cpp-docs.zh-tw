---
title: "independent_bits_engine 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- independent_bits_engine
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 17
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
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: ca810e4918a31ebfbe6217de0eb3cc2f786188ac
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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
  
## <a name="members"></a>Members  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 此範本類別描述一個「引擎配接器」(engine adaptor)*`W`，此配接器會將來自其基底引擎所傳回值的位元重新封裝來產生值，而導致產生 * 位元值。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)


