---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180780"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Microsoft 專屬**

結構 **_com_error**物件。

## <a name="syntax"></a>語法

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>參數

*工時*<br/>
HRESULT 資訊。

*perrinfo*<br/>
`IErrorInfo` 物件。

*fAddRef*<br/>
預設會使此函式在非 null 的 `IErrorInfo` 介面上呼叫 AddRef。 這會在將介面擁有權傳遞至 **_com_error**物件的一般情況下，提供正確的參考計數，例如：

```cpp
throw _com_error(hr, perrinfo);
```

如果您不想讓程式碼將擁有權轉移給 **_com_error**物件，而 `AddRef` 需要在 **_com_error**的析構函式中位移 `Release`，請依照下列方式來建立物件：

```cpp
_com_error err(hr, perrinfo, true);
```

*對於*<br/>
現有的 **_com_error**物件。

## <a name="remarks"></a>備註

第一個函式會建立新的物件，並指定 HRESULT 和選擇性的 `IErrorInfo` 物件。 第二個會建立現有 **_com_error**物件的複本。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
