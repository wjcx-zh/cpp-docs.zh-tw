---
title: is_trivially_copy_assignable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953962"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 類別

測試類型是否有 trivial 複製指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是具有 trivial 複製指派運算子，否則為 false 的類別。

類別的指派建構函式*T*微不足道，如果它以隱含方式提供，類別*T*沒有虛擬函式類別*T*沒有虛擬基底類別類別類型的所有非靜態資料成員都有 trivial 指派運算子和陣列的類別類型的所有非靜態資料成員的類別具有 trivial 指派運算子。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
