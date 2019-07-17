---
title: is_error_condition_enum 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 213970d6260eaf55ac1bd678e6317cf2346ed9bc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245172"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum 類別

代表針對 [error_condition](../standard-library/error-condition-class.md) 列舉進行測試的類型述詞。

## <a name="syntax"></a>語法

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>備註

如果類型 `_Enum` 是適合在 `error_condition` 類型的物件中儲存的列舉值，此[類型述詞](../standard-library/type-traits.md)執行個體的值就會是 true。

允許針對使用者定義的類型將特製化新增到此類型。

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
