---
title: is_standard_layout 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: fba77be22796f3cb5495543d262dd270ac13d598
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560591"
---
# <a name="is_standard_layout-class"></a>is_standard_layout 類別

測試類型是否為標準配置。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型

## <a name="remarks"></a>備註

如果類型 *Ty* 是在記憶體中具有成員物件標準配置的類別，則此類型述詞的實例會保留 true，否則會保留 false。

## <a name="requirements"></a>規格需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
