---
title: is_trivially_copy_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447983"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible 類別

測試類型是否有極簡複製 (trivial copy) 建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是具有簡單式複製參數的類別, 則類型述詞的實例為 true, 否則為 false。

類別*t*的複製函式如果是隱含宣告的, 類別 t 沒有虛擬函數或虛擬基底, 類別*t*的所有直接基底都有簡單的複製函式, 也就是所有非靜態資料成員的類別類別類型的具有簡單的複製函式, 而類別之類型陣列的所有非靜態資料成員的類別具有簡單的複製函數。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
