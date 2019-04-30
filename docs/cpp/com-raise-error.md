---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 5790fceef26d6de4edff604270cc7108f764aced
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399248"
---
# <a name="comraiseerror"></a>_com_raise_error

**Microsoft 專屬**

會擲回[_com_error](../cpp/com-error-class.md)以回應失敗。

## <a name="syntax"></a>語法

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>參數

*hr*<br/>
HRESULT 資訊。

*perrinfo*<br/>
`IErrorInfo` 物件

## <a name="remarks"></a>備註

**_com_raise_error**，其定義於\<comdef.h >，可由相同的名稱和原型的使用者撰寫版本取代。 如果您要使用 `#import`，但是不想要使用 C++ 例外狀況處理，則可以這樣做。 在此情況下，使用者版本 **_com_raise_error**可能會決定進行`longjmp`或顯示訊息方塊並暫止。 不過，使用者版本不應傳回，因為編譯器 COM 支援程式碼不會預期它傳回。

您也可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)來取代預設錯誤處理函式。

根據預設， **_com_raise_error**定義如下：

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭：** \<comdef.h >

**Lib:** 如果**wchar_t 是原生型別**編譯器選項已開啟，請使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 是原生型別**已關閉，請使用 comsupp.lib。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>另請參閱

[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)