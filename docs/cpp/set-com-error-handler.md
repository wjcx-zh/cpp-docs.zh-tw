---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 864236e86b4aeb6ce7b3315df57af1b577693c26
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954935"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler

**Microsoft 專屬**

取代 COM 錯誤處理所使用的預設函式。

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

*hr*<br/>
HRESULT 資訊。

*perrinfo*<br/>
`IErrorInfo` 物件

## <a name="remarks"></a>備註

根據預設， [_com_raise_error](../cpp/com-raise-error.md)會處理所有 COM 錯誤。 您可以使用來變更此行為 **_set_com_error_handler**呼叫您自己的錯誤處理函式。

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

**標頭：** \<comdef.h >

**Lib:** 如果 **/zc: wchar_t**編譯器選項指定 （預設值），使用 comsuppw.lib 或 comsuppwd.lib。 如果 **/zc: wchar_t-** 指定編譯器選項，請使用 comsupp.lib。 如需詳細資訊，包括如何設定此選項，在 IDE 中，請參閱[/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
