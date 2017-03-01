---
title: "&lt;vector&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bb62c0c4e5b2965438539b17ec5a2c465e647ed7
ms.lasthandoff: 02/24/2017

---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函式

  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>  swap  
 交換兩個向量的項目。  
  
```  
template <class Type, class Allocator>  
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供待交換項目的向量，或其項目要與向量 ` left` 交換的向量。  
  
 ` left`  
 其項目要與向量 ` right` 交換的向量。  
  
### <a name="remarks"></a>備註  
 樣板函式是容器類別向量的特製化演算法，以執行成員函式 ` left.` [vector::swap](../standard-library/vector-class.md) *( right*)。 這是編譯器所執行函式樣板部分排序的執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。  
  
### <a name="example"></a>範例  
  如需使用 `swap` 的樣板版本的範例，請參閱成員函式 [vector::swap](../standard-library/vector-class.md) 的程式碼範例。  
  
## <a name="see-also"></a>另請參閱  
 [\<vector>](../standard-library/vector.md)


