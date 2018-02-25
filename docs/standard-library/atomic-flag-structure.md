---
title: "atomic_flag 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8774bcc4b95e2b5c0160843100405f33010b98b6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="atomicflag-structure"></a>atomic_flag 結構
描述以不可部分完成方式設定和清除 `bool` 旗標的物件。 不可部分完成的旗標之作業永遠是無鎖定。  
  
## <a name="syntax"></a>語法  
  
```
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
  
##  <a name="clear"></a>  atomic_flag::clear
 在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 條件約束內，將儲存在 `*this` 中的 `bool` 旗標設定為 `false`。  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。  
  
##  <a name="test_and_set"></a>  atomic_flag::test_and_set
 在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 條件約束內，將儲存在 `*this` 中的 `bool` 旗標設定為 `true`。  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。  
  
### <a name="return-value"></a>傳回值  
 儲存於 `*this` 之旗標的初始值。  
  
## <a name="see-also"></a>請參閱  
 [\<atomic>](../standard-library/atomic.md)



