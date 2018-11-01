---
title: is_trivially_destructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 61d626c308338595a64031a45908ab299ae1a957
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656062"
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible 類別

測試類型是否是可透過極簡方式損壞的類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是易損壞的類型，且編譯器已知解構函式使用任何非 trivial 作業。 否則值會是 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
