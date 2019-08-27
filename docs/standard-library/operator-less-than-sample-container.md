---
title: operator&lt; (&lt;範例容器&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: a286833d96e913a66240d25798e1cc230adf58b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458730"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;範例容器&gt;)

> [!NOTE]
> 本主題位於 Microsoft C++檔中, 做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載 **operator<** 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>傳回值

傳回 `lexicographical_compare(left.begin, left.end, right.begin, right.end)`。

## <a name="see-also"></a>另請參閱

[\<sample container>](../standard-library/sample-container.md)\
[起點](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)