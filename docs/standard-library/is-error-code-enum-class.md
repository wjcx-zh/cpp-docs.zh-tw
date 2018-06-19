---
title: is_error_code_enum 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7024817c5a02d7c4a529167ca65a292b34be119
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844597"
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
