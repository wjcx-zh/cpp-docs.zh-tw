---
title: "subtract_with_carry_engine 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- subtract_with_carry_engine
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- subtract_with_carry_engine class
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: c73401963b231883d26aa45590a9cad305b13875
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine 類別
使用帶進位減法 (延隔 Fibonacci) 演算法，以產生隨機序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### <a name="parameters"></a>參數  
 `UIntType`  
 不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
 `W`  
 **字組大小**。 狀態序列的每個字組大小 (位元)。 **前置條件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **短延隔**。 整數值數目。 **前置條件**：`0 < S < R`  
  
 `R`  
 **長延隔**。 決定所產生數列中的週期。  
  
## <a name="members"></a>Members  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` 是一個成員常數，定義為 `19780503u`，用做 `subtract_with_carry_engine::seed` 的預設參數值以及單一值建構函式。|||  
  
 如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 `substract_with_carry_engine` 樣板類別是針對 [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md) 的改良。 但這些引擎都不像 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md) 一樣快，且具有高品質的結果。  
  
 此引擎會使用週期關聯 ( *period*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` 來產生使用者指定的不帶正負號整數類型值，其中，如果 `x(i - S) - x(i - R) - cy(i - 1) < 0`，則 `cy(i)` 的值為 `1`，否則為 `0`，而`M` 的值為 `2`<sup>W</sup>。引擎的狀態是一個進位指標加上 `R` 值。 這些值包含已至少呼叫 `R` `operator()` 次時所傳回的最後一個 `R` 值，否則為已傳回的 `N` 值，以及種子的最後一個 `R - N` 值。  
  
 範本引數 `UIntType` 必須夠大，才能保留最多 `M - 1` 個值。  
  
 雖然您可以直接從此引擎建構產生器，但您也可以使用下列其中一個預先定義的 typedef：  
  
 `ranlux24_base`：用來做為 `ranlux24` 的基底。                   
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`：用來做為 `ranlux48` 的基底。                   
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 如需帶進位減法引擎演算法的詳細資訊，請參閱維基百科文章：[延隔 Fibonacci 產生器 (英文)](http://go.microsoft.com/fwlink/LinkId=402445)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)


