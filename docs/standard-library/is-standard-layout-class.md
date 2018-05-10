---
title: is_standard_layout 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d899d9c56ecc8b27b18498de225bbba6f0d110d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
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
|`Ty`|要查詢的類型|

## <a name="remarks"></a>備註

如果類型 `Ty` 在記憶體中是具有成員物件之標準配置的類別，則類型述詞的執行個體會保留 true，否則保留 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
