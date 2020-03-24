---
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 1d0ad8727dd4d5ec06a45ec26c67dd3ad268f524
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189517"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Microsoft 專屬**

將 `BSTR` 值轉換成 `char *`。

## <a name="syntax"></a>語法

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>參數

*.Psrc*<br/>
BSTR 變數。

## <a name="remarks"></a>備註

**ConvertBSTRToString**會配置您必須刪除的字串。

## <a name="example"></a>範例

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h. h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： Wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
