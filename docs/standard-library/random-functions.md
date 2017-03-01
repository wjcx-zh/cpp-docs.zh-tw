---
title: "&lt;random&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 3aebef535acb59046fab53d49051df16bd362c3c
ms.lasthandoff: 02/24/2017

---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函式
  
##  <a name="a-namegeneratecanonicala--generatecanonical"></a><a name="generate_canonical"></a>  generate_canonical  
 從隨機序列傳回浮點值。  
  
> [!NOTE]
>  ISO C++ 標準規定此函式應傳回範圍 [`0`, `1`) 中的值。 Visual Studio 尚未與此條件約束相容。 作為在此範圍中產生值的解決辦法，請使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md)。  
  
```  
template <class RealType, size_t Bits, class Generator>  
RealType generate_canonical(Generator& Gen);
```  
  
### <a name="parameters"></a>參數  
 `RealType`  
 浮點整數類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
 `Bits`  
 亂數產生器。  
  
 `Gen`  
 亂數產生器。  
  
### <a name="remarks"></a>備註  
 範本函式會重複呼叫 `operator()` 的 `Gen`，並將傳回的值封裝到類型 `x` 的浮點值 `RealType` 中，直到其在 `x` 中收集到指定的尾數位元數為止。 指定的數是 `Bits` (其必須為非零值) 的較小值，以及 `RealType` 中尾數位元的完整數。 第一次呼叫會提供最低位位元數。 函式會傳回 `x`。  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)


