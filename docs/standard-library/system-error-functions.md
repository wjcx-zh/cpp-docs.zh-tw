---
title: '&lt;system_error&gt; 函式'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245108"
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函式

## <a name="generic_category"></a> generic_category

代表泛型錯誤的分類。

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>備註

`generic_category`物件會實作[error_category](../standard-library/error-category-class.md)。

## <a name="is_error_code_enum_v"></a> is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a> is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a> make_error_code

建立錯誤碼物件。

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>參數

*錯誤*\
`std::errc`存放於錯誤的程式碼物件中的列舉值。

### <a name="return-value"></a>傳回值

錯誤碼物件。

### <a name="remarks"></a>備註

## <a name="make_error_condition"></a> make_error_condition

建立錯誤條件物件。

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>參數

*錯誤*\
`std::errc`存放於錯誤的程式碼物件中的列舉值。

### <a name="return-value"></a>傳回值

錯誤條件物件。

### <a name="remarks"></a>備註

## <a name="system_category"></a> system_category

代表低階系統溢位所造成的錯誤分類。

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>備註

`system_category`物件會實作[error_category](../standard-library/error-category-class.md)。
