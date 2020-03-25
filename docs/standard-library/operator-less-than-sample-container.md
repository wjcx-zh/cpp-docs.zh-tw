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
ms.openlocfilehash: 6ef43fb762c4da71062fc846048f21c0112bfafc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215263"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;範例容器&gt;)

> [!NOTE]
> 本主題位於 Microsoft C++檔中，做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載**運算子 <** 來比較類別樣板[容器](../standard-library/sample-container-class.md)的兩個物件。

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
[開始](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)
