---
title: operator&lt;= (&lt;範例容器&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
ms.openlocfilehash: 78d49f82f39bc0e96f88ffdcad2cde8a20b0f123
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221377"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt;= (&lt;範例容器&gt;)

> [!NOTE]
> 本主題位於 MicrosoftC++中所用容器的無作用範例文件C++標準程式庫。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載 **operator<=** 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
bool operator<=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>傳回值

傳回 `!(right < left)`。

## <a name="see-also"></a>另請參閱

[\<範例容器>](../standard-library/sample-container.md)<br/>
