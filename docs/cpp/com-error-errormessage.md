---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180663"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 專屬**

抓取儲存在 `_com_error` 物件中之 HRESULT 的字串訊息。

## <a name="syntax"></a>語法

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 HRESULT 的字串訊息。 如果 HRESULT 是對應的16位[wCode](../cpp/com-error-wcode.md)，則會傳回一般訊息「`IDispatch error #<wCode>`」。 如果找不到訊息，則會傳回一般訊息「`Unknown error #<hresult>`」。 傳回的字串會是 Unicode 字串或多位元組字串，視 _UNICODE 巨集的狀態而定。

## <a name="remarks"></a>備註

針對在 `_com_error` 物件內記錄的 HRESULT，抓取適當的系統郵件內文。 系統郵件內文是藉由呼叫 Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)函數來取得。 傳回的字串會由 `FormatMessage` API 配置，並且在終結 `_com_error` 物件時釋放。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
