---
title: is_error_code_enum 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: d890eb6a1b7c93f9ae5b87018c3bf1d6eeae8abb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336476"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum 類別

代表針對 [error_code](../standard-library/error-code-class.md) 列舉進行測試的類型述詞。

## <a name="syntax"></a>語法

```cpp
template <_Enum>
class is_error_code_enum;
```

## <a name="remarks"></a>備註

如果類型 `_Enum` 是適合在 `error_code` 類型的物件中儲存的列舉值，此[類型述詞](../standard-library/type-traits.md)執行個體的值就會是 true。

允許針對使用者定義的類型將特製化新增到此類型。

## <a name="requirements"></a>需求

**標頭：**\<system_error>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
