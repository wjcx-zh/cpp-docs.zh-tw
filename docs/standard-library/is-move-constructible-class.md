---
title: is_move_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508988"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 類別

測試類型是否具有移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要評估的類型

## <a name="remarks"></a>備註

類型述詞評估為 true 的型別*T*可以藉由使用移動作業建構。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
