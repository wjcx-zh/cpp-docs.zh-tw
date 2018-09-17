---
title: '&lt;vector&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: 71594b225c950714d8b9aba169e68804033c93a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700748"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函式


## <a name="swap"></a>  swap

交換兩個向量的項目。

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*<br/>
提供要交換之元素的向量或其項目要與向量交換的向量*左*。

*left*<br/>
其項目要與向量交換的向量*右*。

### <a name="remarks"></a>備註

範本函式是容器類別向量，來執行成員函式特製化的演算法`left`。 [vector:: swap](../standard-library/vector-class.md) *(右*)。 這是編譯器所執行函式樣板部分排序的執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的樣板版本的範例，請參閱成員函式 [vector::swap](../standard-library/vector-class.md) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[\<vector>](../standard-library/vector.md)<br/>
