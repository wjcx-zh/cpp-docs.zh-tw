---
title: atomic_flag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06959bd5a22c65077f447f0f0e776025cbe5ced5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="atomicflag-structure"></a>atomic_flag 結構

描述以不可部分完成方式設定和清除 `bool` 旗標的物件。 不可部分完成的旗標之作業永遠是無鎖定。

## <a name="syntax"></a>語法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[clear](#clear)|將已儲存的旗標設定為 `false`。|
|[test_and_set](#test_and_set)|將已儲存的旗標設定為 `true` 並傳回初始旗標值。|

## <a name="remarks"></a>備註

`atomic_flag` 物件可以傳遞至非成員函式 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 這些非成員函式可以透過使用 `ATOMIC_FLAG_INIT` 值初始化。

## <a name="requirements"></a>需求

**標頭：** \<不可部分完成 >

**命名空間：** std

## <a name="clear"></a>  atomic_flag::clear

在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 條件約束內，將儲存在 `*this` 中的 `bool` 旗標設定為 `false`。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="test_and_set"></a>  atomic_flag::test_and_set

在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 條件約束內，將儲存在 `*this` 中的 `bool` 旗標設定為 `true`。

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

儲存於 `*this` 之旗標的初始值。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)<br/>
