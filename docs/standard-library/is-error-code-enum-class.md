---
title: is_error_code_enum 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: bc4ed7cd2e058414448c9366011b9efab97ee3d5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245182"
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

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
