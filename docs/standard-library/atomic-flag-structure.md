---
title: atomic_flag 結構
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ff60e05c7d14104e164e8251a9146f8b0d0dcde3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203919"
---
# <a name="atomic_flag-structure"></a>atomic_flag 結構

描述可自動設定和清除旗標的物件 **`bool`** 。 不可部分完成的旗標之作業永遠是無鎖定。

## <a name="syntax"></a>語法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[明確](#clear)|將儲存的旗標設定為 **`false`** 。|
|[test_and_set](#test_and_set)|將儲存的旗標設定為 **`true`** ，並傳回初始旗標值。|

## <a name="remarks"></a>備註

`atomic_flag` 物件可以傳遞至非成員函式 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 這些非成員函式可以透過使用 `ATOMIC_FLAG_INIT` 值初始化。

## <a name="requirements"></a>需求

**標頭：**\<atomic>

**命名空間：** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag：： clear

將 **`bool`** 儲存在中的旗標設定 **`*this`** 為 **`false`** 指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束內的。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*即可*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag：： test_and_set

將 **`bool`** 儲存在中的旗標設定 **`*this`** 為 **`true`** 指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束內的。

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*即可*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

儲存在中之旗標的初始值 **`*this`** 。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)
