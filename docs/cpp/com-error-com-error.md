---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631734"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Microsoft 專屬**

建構 **_com_error**物件。

## <a name="syntax"></a>語法

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>參數

*hr*<br/>
HRESULT 資訊。

*perrinfo*<br/>
`IErrorInfo` 物件

*fAddRef*<br/>
預設值會導致非 null 值上呼叫 AddRef 的建構函式`IErrorInfo`介面。 這會提供正確的參考計數介面的擁有權會傳遞至的常見案例 **_com_error**物件，例如：

```cpp
throw _com_error(hr, perrinfo);
```

如果您不想要傳送擁有權轉移給您的程式碼 **_com_error**物件，而`AddRef`才能位移`Release`中 **_com_error**解構函式，建構的物件如下所示：

```cpp
_com_error err(hr, perrinfo, true);
```

*,*<br/>
將現有 **_com_error**物件。

## <a name="remarks"></a>備註

第一個建構函式會建立新的物件，指定的 HRESULT 和選擇性`IErrorInfo`物件。 第二個建立的現有複本 **_com_error**物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)