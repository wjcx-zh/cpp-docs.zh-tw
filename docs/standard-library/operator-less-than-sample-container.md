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
ms.openlocfilehash: 57796cc69dd734ea4c619db4bd8fedbfa09ce15b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371307"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;範例容器&gt;)

> [!NOTE]
> 本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

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

[\<範例容器>](../standard-library/sample-container.md)<br/>
[begin](../standard-library/container-class-begin.md)<br/>
[end](../standard-library/container-class-end.md)