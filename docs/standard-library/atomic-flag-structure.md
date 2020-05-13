---
title: atomic_flag 結構
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376862"
---
# <a name="atomic_flag-structure"></a>atomic_flag 結構

描述以原子方式設置和清除**布爾**標誌的物件。 不可部分完成的旗標之作業永遠是無鎖定。

## <a name="syntax"></a>語法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[清楚](#clear)|將儲存的標誌設為**false**。|
|[test_and_set](#test_and_set)|將儲存的標誌設定為**true**並返回初始標誌值。|

## <a name="remarks"></a>備註

`atomic_flag` 物件可以傳遞至非成員函式 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 這些非成員函式可以透過使用 `ATOMIC_FLAG_INIT` 值初始化。

## <a name="requirements"></a>需求

**標題:**\<原子>

**命名空間：** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::清除

將儲存在`*this`中的**bool**標誌設定為**false,** 在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束中。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag:test_and_set

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束中將儲存`*this`在中的**bool**標誌設定為**true。**

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

儲存於 `*this` 之旗標的初始值。

## <a name="see-also"></a>另請參閱

[\<原子>](../standard-library/atomic.md)
