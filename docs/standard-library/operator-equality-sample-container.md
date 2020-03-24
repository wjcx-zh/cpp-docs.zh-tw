---
title: operator== (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 08adfcc770551d3050daa46c870b950e468c95b3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150638"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> 本主題位於 Microsoft C++檔中，做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載 `operator==` 來比較類別樣板[容器](../standard-library/sample-container-class.md)的兩個物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>傳回值

傳回 `== right.size && equal(left.`[開始](../standard-library/container-class-begin.md)`, left.`[結束](../standard-library/container-class-end.md)`, right.begin)``left.`[大小](../standard-library/container-class-size.md)。

## <a name="see-also"></a>另請參閱

[\<範例容器>](../standard-library/sample-container.md)
