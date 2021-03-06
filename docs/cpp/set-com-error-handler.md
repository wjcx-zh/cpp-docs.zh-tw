---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: debad733f351c710ada342e29fa95a4d1ff03b7d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749802"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

取代 COM 錯誤處理所使用的預設函式。 **_set_com_error_handler**特定於微軟。

## <a name="syntax"></a>語法

```cpp
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

*人力資源*<br/>
HRESULT 資訊。

*佩里info*<br/>
`IErrorInfo` 物件。

## <a name="remarks"></a>備註

預設情況下[,_com_raise_error](../cpp/com-raise-error.md)處理所有 COM 錯誤。 您可以使用 **_set_com_error_handler**來呼叫自己的錯誤處理函數來更改此行為。

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

**標題:** \<comdef.h>

**Lib:** 如果指定 **/Zc:wchar_t**編譯器選項(預設值),請使用 comsuppw.lib 或 comsuppwd.lib。 如果指定了 **/Zc:wchar_t-** 編譯器選項,請使用 comsupp.lib。 有關詳細資訊(包括如何在IDE中設置此選項),請參閱[/Zc:wchar_t (wchar_t本機類型)。](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
