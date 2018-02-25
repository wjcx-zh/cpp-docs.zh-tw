---
title: "vector&lt;bool&gt;::reference 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 56101a717c56a3999ad32648de8f9ae75d7439d0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference 類別
`vector<bool>::reference` 類別是 [vector\<bool> 類別](../standard-library/vector-bool-class.md)提供的 Proxy 類別，用來模擬 `bool&`。  
  
## <a name="remarks"></a>備註  
 需要模擬參考，因為 C++ 原生不允許對位元的直接參考。 `vector<bool>` 對每個項目只使用一個位元，您可以使用這個 Proxy 類別來參考位元。 不過，因為某些指派無效，參考模擬不完整。 例如，因為 `vector<bool>::reference` 物件位址無法採用，使用 [vector\<bool>::operator&#91;&#93;](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd) 的下列程式碼不正確：  
  
```cpp  
vector<bool> vb;  
// ...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[flip](../standard-library/vector-bool-reference-flip.md)|反轉向量項目的布林值。|  
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供從 `vector<bool>::reference` 至 `bool` 的隱含轉換。|  
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|將布林值指派給位元，或是將參考的項目所表示的值指派給位元。|  
  
## <a name="requirements"></a>需求  
 **標頭**：\<vector>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [\<vector>](../standard-library/vector.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

