---
title: is_trivially_default_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 19a5e8afedf3e59d5dafa937af4f7d35343eb7d9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459645"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 類別

測試類型是否有 trivial 預設建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是具有簡單的函式的類別, 則類型述詞的實例會保留 true, 否則會保留 false。

在下列情況下, 類別*Ty*的預設的函式是簡單的:

- 它是以隱含方式宣告的預設建構函式

- 類別*Ty*沒有虛擬函式

- 類別*Ty*沒有虛擬基底

- 類別*Ty*的所有直接基底都有簡單的函式

- 類別類型的所有非靜態資料成員的類別都具有 trivial 建構函式

- 類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 建構函式

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
