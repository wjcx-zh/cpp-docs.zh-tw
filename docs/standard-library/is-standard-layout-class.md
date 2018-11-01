---
title: is_standard_layout 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 75691c1b09b71580474cc22cdc8382bff55a5e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500278"
---
# <a name="isstandardlayout-class"></a>is_standard_layout 類別

測試類型是否為標準配置。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Ty*|要查詢的類型|

## <a name="remarks"></a>備註

如果這個型別述詞執行個體保留 true 的型別*Ty*是具有成員物件的標準版面配置在記憶體中，否則為 false 的類別。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
