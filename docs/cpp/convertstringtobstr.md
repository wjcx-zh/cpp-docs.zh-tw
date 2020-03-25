---
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 2065011ee6bbf98ce2c83be494f1e6631af9f7cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170705"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Microsoft 專屬**

將 `char *` 值轉換成 `BSTR`。

## <a name="syntax"></a>語法

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>參數

*.Psrc*<br/>
`char *` 變數。

## <a name="example"></a>範例

```cpp
// ConvertStringToBSTR.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")
#pragma comment(lib, "kernel32.lib")

int main() {
   char* lpszText = "Test";
   printf_s("char * text: %s\n", lpszText);

   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);
   wprintf_s(L"BSTR text: %s\n", bstrText);

   SysFreeString(bstrText);
}
```

```Output
char * text: Test
BSTR text: Test
```

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h. h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： Wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
