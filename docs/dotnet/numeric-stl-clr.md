---
title: numeric (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 0311b36ec1190631e053eeade443939703e69103
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328899"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)

定義容器樣板函式可執行數值處理提供的演算法。

## <a name="syntax"></a>語法

```
#include <cliext/numeric>
```

## <a name="requirements"></a>需求

**標頭：** \<cliext/數字 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|功能|描述|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|藉由計算連續的部分總和來計算指定範圍內所有元素 (包括某個初始值) 的總和，或是計算連續部分結果 (同樣是使用指定的二進位運算而非加總來計算出) 的結果。|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。|
|[inner_product (STL/CLR)](#inner_product)|計算兩個範圍的元素乘積總和並將它加到指定的初始值，或計算一般化程序的結果，其中總和及乘積二進位運算會由其他指定的二進位運算取代。|
|[partial_sum (STL/CLR)](#partial_sum)|計算一系列總和，在輸入範圍中從第一個項目到`i`個項目，並將每個總和的結果`i`個項目，在目的範圍的或計算一般化程序的結果，其中總和運算由另一個指定的二進位運算取代。|

## <a name="members"></a>成員

## <a name="accumulate"></a> accumulate (STL/CLR)

藉由計算連續的部分總和來計算指定範圍內所有元素 (包括某個初始值) 的總和，或是計算連續部分結果 (同樣是使用指定的二進位運算而非加總來計算出) 的結果。

### <a name="syntax"></a>語法

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>備註

此函式的行為與 c + + 標準程式庫的數值函式相同`accumulate`。 如需詳細資訊，請參閱 <<c0> [ 累積](../standard-library/numeric-functions.md#accumulate)。

## <a name="adjacent_difference"></a> adjacent_difference (STL/CLR)

計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。

### <a name="syntax"></a>語法

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>備註

此函式的行為與 c + + 標準程式庫的數值函式相同`adjacent_difference`。 如需詳細資訊，請參閱 < [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)。

## <a name="inner_product"></a> inner_product (STL/CLR)

計算兩個範圍的元素乘積總和並將它加到指定的初始值，或計算一般化程序的結果，其中總和及乘積二進位運算會由其他指定的二進位運算取代。

### <a name="syntax"></a>語法

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>備註

此函式的行為與 c + + 標準程式庫的數值函式相同`inner_product`。 如需詳細資訊，請參閱 < [inner_product](../standard-library/numeric-functions.md#inner_product)。

## <a name="partial_sum"></a> partial_sum (STL/CLR)

計算一系列總和，在輸入範圍中從第一個項目到`i`個項目，並將每個總和的結果`i`個項目，在目的範圍的或計算一般化程序的結果，其中總和運算由另一個指定的二進位運算取代。

### <a name="syntax"></a>語法

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>備註

此函式的行為與 c + + 標準程式庫的數值函式相同`partial_sum`。 如需詳細資訊，請參閱 < [partial_sum](../standard-library/numeric-functions.md#partial_sum)。