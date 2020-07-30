---
title: '&lt;vector&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: bf28e44b4f603b1e4d6a87f0c28b42d6cc159980
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224548"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函式

## <a name="swap"></a><a name="swap"></a>調換

交換兩個向量的項目。

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*再*\
提供要交換之元素的向量，或其專案要與所*遺留*之向量交換的向量。

*左面*\
其元素要與向量*許可權*的向量交換的向量。

### <a name="remarks"></a>備註

範本函式是在容器類別向量上特製化的演算法，用來執行成員函式 `left` 。 [vector：： swap](../standard-library/vector-class.md) *（right*）。 這是編譯器所執行函式樣板部分排序的執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 在演算法類別中，樣板函式的一般版本 **`template`** \< **class T**> （ **void swap**（ **t&**， **t&**）會依指派運作，而且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的樣板版本的範例，請參閱成員函式 [vector::swap](../standard-library/vector-class.md) 的程式碼範例。
