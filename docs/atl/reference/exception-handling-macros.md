---
title: 異常處理宏
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330092"
---
# <a name="exception-handling-macros"></a>異常處理宏

這些宏支援異常處理。

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|語句處理關聯的`_ATLTRY`中發生的錯誤。|
|[_ATLCATCHALL](#_atlcatchall)|語句處理關聯的`_ATLTRY`中發生的錯誤。|
|[_ATLTRY](#_atltry)|標記可能發生錯誤的受保護代碼部分。|

## <a name="requirements"></a>需求：

**標題:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

語句處理關聯的`_ATLTRY`中發生的錯誤。

```
_ATLCATCH(e)
```

### <a name="parameters"></a>參數

*e*<br/>
要捕獲的異常。

### <a name="remarks"></a>備註

與一起使用`_ATLTRY`。 解析為處理給定類型的C++異常C++ [catch(CAtlexception e)。](../../cpp/try-throw-and-catch-statements-cpp.md)

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

語句處理關聯的`_ATLTRY`中發生的錯誤。

```
_ATLCATCHALL
```

### <a name="remarks"></a>備註

與一起使用`_ATLTRY`。 解析為處理所有類型的C++異常C++ [catch(...)。](../../cpp/try-throw-and-catch-statements-cpp.md)

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

標記可能發生錯誤的受保護代碼部分。

```
_ATLTRY
```

### <a name="remarks"></a>備註

與[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)一起使用。 解析為C++符號[嘗試](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
