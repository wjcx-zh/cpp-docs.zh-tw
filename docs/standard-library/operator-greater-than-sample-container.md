---
title: operator&gt; (&lt;範例容器&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
ms.openlocfilehash: 80bcc6b81ec7d6771895f711d61a507f057eae2a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689192"
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;範例容器&gt;)

> [!NOTE]
> 本主題位於 Microsoft C++檔中，做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載**運算子 >** 來比較類別樣板[容器](../standard-library/sample-container-class.md)的兩個物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
bool operator*gt;(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>傳回值

傳回 `right < left`。

## <a name="see-also"></a>請參閱

[\<範例容器>](../standard-library/sample-container.md)
