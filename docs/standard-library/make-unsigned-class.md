---
title: make_unsigned 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37f121912a13d6e4dac1692d2dab1b5ffd34bd6d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="makeunsigned-class"></a>make_unsigned 類別

建立類型，或是建立大於或等於類型大小的最小無正負號類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`T`|要修改的類型。|

## <a name="remarks"></a>備註

如果 `is_unsigned<T>` 為 true，則 modifier 類型的執行個體所保留的修改類型是 `T`。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
