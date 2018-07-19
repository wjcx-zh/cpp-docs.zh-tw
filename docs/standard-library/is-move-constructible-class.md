---
title: is_move_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 979e726e1374ac37844472d9e2f9ae8ddd5ddf4d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965798"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 類別

測試類型是否具有移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T*来評估的型別

## <a name="remarks"></a>備註

類型述詞評估為 true 的型別*T*可以藉由使用移動作業建構。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
