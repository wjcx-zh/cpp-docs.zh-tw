---
title: is_trivially_move_assignable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae0db2b789e16a39396a329a64dfb8794eef5775
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961905"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 類別

測試類型是否有 trivial 移動指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有 trivial 移動指派運算子，否則為 false 的類別。

類別的移動指派運算子*Ty*輕而易舉的事如果：

它會隱含地提供

此類別*Ty*沒有虛擬函式

此類別*Ty*沒有虛擬基底

類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子

類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
