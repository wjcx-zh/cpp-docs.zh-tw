---
title: atomic_flag 結構
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 13af0c26b765aa7ebbbd1ec22b5a0ed1b8cce0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550419"
---
# <a name="atomicflag-structure"></a>atomic_flag 結構

描述的物件，以不可分割方式設定，並清除**bool**旗標。 不可部分完成的旗標之作業永遠是無鎖定。

## <a name="syntax"></a>語法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[clear](#clear)|若要設定儲存的旗標**false**。|
|[test_and_set](#test_and_set)|若要設定儲存的旗標 **，則為 true** ，並傳回初始旗標值。|

## <a name="remarks"></a>備註

`atomic_flag` 物件可以傳遞至非成員函式 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 這些非成員函式可以透過使用 `ATOMIC_FLAG_INIT` 值初始化。

## <a name="requirements"></a>需求

**標頭：** \<不可部分完成 >

**命名空間：** std

## <a name="clear"></a>  atomic_flag::clear

集合**bool**旗標，會儲存在`*this`要**false**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*順序*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="test_and_set"></a>  atomic_flag::test_and_set

集合**bool**旗標，會儲存在`*this`要 **，則為 true**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>參數

*順序*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

儲存於 `*this` 之旗標的初始值。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)<br/>
