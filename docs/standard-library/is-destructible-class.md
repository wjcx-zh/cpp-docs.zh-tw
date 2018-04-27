---
title: is_destructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 887946156084d962debf569fc4f23f45dea18293
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="isdestructible-class"></a>is_destructible 類別

測試類型是否為易損壞的。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

## <a name="remarks"></a>備註

如果類型 `T` 是易損壞的類型，則類型述詞的執行個體為 true，否則為 false。 易損壞的類型是指參考類型、物件類型和類型，其中某些類型的 `U` 等於 `remove_all_extents_t<T>` ，且未經過評估的運算元 `std::declval<U&>.~U()` 是語式正確的。 不完整的類型、 `void`及函式類型等其他類型，則不屬於易損壞的類型。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
