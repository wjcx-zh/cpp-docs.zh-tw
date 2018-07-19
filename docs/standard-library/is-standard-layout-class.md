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
ms.openlocfilehash: 6223151acbce299178101735db05f7b4bd516f2f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965509"
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
