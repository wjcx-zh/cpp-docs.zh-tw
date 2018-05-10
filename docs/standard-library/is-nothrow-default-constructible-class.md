---
title: is_nothrow_default_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bf12a91fc4dd1485e0129e8ce9049d3401c181c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible 類別

測試類型是否有非擲回預設建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>參數

`Ty` 要查詢的類型。

## <a name="remarks"></a>備註

如果類型 `Ty` 具有非擲回預設建構函式，則述詞類型的執行個體會保存 true，否則保存 false。 類型述詞的執行個體相當於 `is_nothrow_constructible<Ty>`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
