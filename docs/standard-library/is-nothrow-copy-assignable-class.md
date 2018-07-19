---
title: is_nothrow_copy_assignable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e540d6fe4c00772af01b187d24efae18fd62357f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957554"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 類別

測試類型是否具有編譯器已知不會擲回的複製指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

類型述詞的執行個體亦適用於可參考的型別*T*其中`is_nothrow_assignable<T&, const T&>`保存 true; 否則為 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable 類別](../standard-library/is-nothrow-assignable-class.md)<br/>
