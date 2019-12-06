---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 226dce24de68edd66ca68c43e41ce0cb5b8a1b48
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857290"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

取代 COM 錯誤處理所使用的預設函式。 **_set_com_error_handler**是 Microsoft 特有的。

## <a name="syntax"></a>語法

```
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>參數

*pHandler*<br/>
取代函式的指標。

*工時*<br/>
HRESULT 資訊。

*perrinfo*<br/>
`IErrorInfo` 物件。

## <a name="remarks"></a>備註

根據預設， [_com_raise_error](../cpp/com-raise-error.md)會處理所有 com 錯誤。 您可以使用 **_set_com_error_handler**呼叫自己的錯誤處理函式，來變更此行為。

取代函式擁有的簽章必須相當於 `_com_raise_error` 的簽章。

## <a name="example"></a>範例

```cpp
// _set_com_error_handler.cpp
// compile with /EHsc
#include <stdio.h>
#include <comdef.h>
#include <comutil.h>

// Importing ado dll to attempt to establish an ado connection.
// Not related to _set_com_error_handler
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")

void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)
{
   throw "Unable to establish the connection!";
}

int main()
{
   _set_com_error_handler(_My_com_raise_error);
   _bstr_t bstrEmpty(L"");
   _ConnectionPtr Connection = NULL;
   try
   {
      Connection.CreateInstance(__uuidof(Connection));
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);
   }
   catch(char* errorMessage)
   {
      printf("Exception raised: %s\n", errorMessage);
   }

   return 0;
}
```

```Output
Exception raised: Unable to establish the connection!
```

## <a name="requirements"></a>需求

**標頭：** \<comdef.h. h >

**Lib：** 如果指定了 **/zc： wchar_t**編譯器選項（預設值），請使用 comsuppw.lib 或 comsuppwd.lib。 如果指定了 **/zc： wchar_t-** 編譯器選項，請使用 comsupp.lib。 如需詳細資訊，包括如何在 IDE 中設定此選項，請參閱[/zc： wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
