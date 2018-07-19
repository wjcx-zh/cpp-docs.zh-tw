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
ms.openlocfilehash: f379500f9455ed9ad9a581966e0f8ed7bfed13f7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953910"
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
|*T*|要修改的類型。|

## <a name="remarks"></a>備註

類型修飾詞的執行個體保留修改的類型所*T*如果`is_unsigned<T>`保存，則為 true。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
