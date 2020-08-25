---
title: 例外狀況處理宏
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 7fcd8221ba5f121749cf366a93cc8a6d8d00ed7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833435"
---
# <a name="exception-handling-macros"></a>例外狀況處理宏

這些宏提供例外狀況處理的支援。

|名稱|描述|
|-|-|
|[_ATLCATCH](#_atlcatch)|語句 (s) 來處理相關聯的中發生的錯誤 `_ATLTRY` 。|
|[_ATLCATCHALL](#_atlcatchall)|語句 (s) 來處理相關聯的中發生的錯誤 `_ATLTRY` 。|
|[_ATLTRY](#_atltry)|標記可能發生錯誤的受防護程式碼區段。|

## <a name="requirements"></a>需求：

**標頭：** atldef。h

## <a name="_atlcatch"></a><a name="_atlcatch"></a> _ATLCATCH

語句 (s) 來處理相關聯的中發生的錯誤 `_ATLTRY` 。

```
_ATLCATCH(e)
```

### <a name="parameters"></a>參數

*pci-e*<br/>
要攔截的例外狀況。

### <a name="remarks"></a>備註

與一起使用 `_ATLTRY` 。 解析為 c + + [catch (CAtlException e) ](../../cpp/try-throw-and-catch-statements-cpp.md) 來處理指定的 c + + 例外狀況類型。

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a> _ATLCATCHALL

語句 (s) 來處理相關聯的中發生的錯誤 `_ATLTRY` 。

```
_ATLCATCHALL
```

### <a name="remarks"></a>備註

與一起使用 `_ATLTRY` 。 解析為 c + + [catch ( ... ) ](../../cpp/try-throw-and-catch-statements-cpp.md) 來處理所有類型的 c + + 例外狀況。

## <a name="_atltry"></a><a name="_atltry"></a> _ATLTRY

標記可能發生錯誤的受防護程式碼區段。

```
_ATLTRY
```

### <a name="remarks"></a>備註

用於搭配 [_ATLCATCH](#_atlcatch) 或 [_ATLCATCHALL](#_atlcatchall)。 解析為 c + + 符號 [try](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
