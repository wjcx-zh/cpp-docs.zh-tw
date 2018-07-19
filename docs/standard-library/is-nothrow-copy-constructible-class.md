---
title: is_nothrow_copy_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc4f839ed955048b96f6327c63cd2cc82fef8aca
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953768"
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible 類別

測試類型是否具有 **nothrow** 複製建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>參數

*Ty*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty* nothrow 複製建構函式，否則為 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
