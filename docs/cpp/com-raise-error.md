---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745089"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft 特定的**

引發[_com_error](../cpp/com-error-class.md)以回應故障。

## <a name="syntax"></a>語法

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>參數

*人力資源*<br/>
HRESULT 資訊。

*佩里info*<br/>
`IErrorInfo` 物件。

## <a name="remarks"></a>備註

**_com_raise_error(** 在 comdef.h>中\<定義)可以替換為同名和原型的使用者編寫的版本。 如果您要使用 `#import`，但是不想要使用 C++ 例外狀況處理，則可以這樣做。 在這種情況下 **,_com_raise_error**的使用者版本可能會決定執行`longjmp`或顯示消息框並停止。 不過，使用者版本不應傳回，因為編譯器 COM 支援程式碼不會預期它傳回。

您還可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)來替換預設的錯誤處理函數。

預設情況下 **,_com_raise_error**的定義如下:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**結束微軟的**

## <a name="requirements"></a>需求

**標題:** \<comdef.h>

**Lib:** 如果**wchar_t是本機類型**編譯器選項,請使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t是本機類型**關閉,請使用 comsupp.lib。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
