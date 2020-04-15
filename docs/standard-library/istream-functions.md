---
title: '&lt;istream&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363071"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 函式

|||
|-|-|
|[交換](#istream_swap)|[Ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>交換

交換兩個資料流物件的元素。

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>參數

*離開*\
資料流。

*對*\
資料流。

## <a name="ws"></a><a name="ws"></a>Ws

略過資料流中的空白字元。

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>參數

*_Istr*\
資料流。

### <a name="return-value"></a>傳回值

資料流。

### <a name="remarks"></a>備註

操縱器提取`ch`並丟棄[use_facet](../standard-library/basic-filebuf-class.md#open)< **型**\<**Elem> >(getloc)** 的任何元素。 [getloc](../standard-library/ios-base-class.md#getloc) **is**( **ctype**\< **Elem**>:: **space**, **ch**) 為 true。

此函數如果在擷取元素時遇到檔案結尾，就會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)。 傳回 *_Istr*。

### <a name="example"></a>範例

如需使用 `ws` 的範例，請參閱 [operator>>](../standard-library/istream-operators.md#op_gt_gt)。

## <a name="see-also"></a>另請參閱

[\<istream>](../standard-library/istream.md)
