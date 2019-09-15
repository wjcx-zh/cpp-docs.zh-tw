---
title: _outp、_outpw、_outpd
ms.date: 11/04/2016
api_name:
- _outpd
- _outp
- _outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: d1e7028ae833e1358ce3199b7e7079535c84d135
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944123"
---
# <a name="_outp-_outpw-_outpd"></a>_outp、_outpw、_outpd

從連接埠輸出一個位元組 (`_outp`)、一個字組 (`_outpw`) 或雙字組 (`_outpd`)。

> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。

> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```

      int _outp(
unsigned short port,
int databyte
);
unsigned short _outpw(
unsigned short port,
unsigned short dataword
);
unsigned long _outpd(
unsigned short port,
unsigned long dataword
);
```

#### <a name="parameters"></a>參數
*連接埠*<br/>
連接埠號碼。

*databyte, dataword*<br/>
輸出值。

## <a name="return-value"></a>傳回值

這些函式會傳回資料輸出。 不會傳回錯誤。

## <a name="remarks"></a>備註

`_outp`、 `_outpw`及 `_outpd` 函式會個別寫入一個位元組、一個字組及雙字組到指定的輸出連接埠。 *port* 引數可以是介於 0 - 65,535 之間任何不帶正負號的整數；*databyte* 可以是介於 0 - 255 之間的任何整數；*dataword* 可以位於整數、不帶正負號之 short 整數，或不帶正負號之 long 整數範圍內的任何值。

由於這些函式直接寫入 I/O 連接埠，因此無法用於使用者程式碼。 如需如何使用這些作業系統中之 I/O 連接埠的資訊，請前往 MSDN 搜尋 "Serial Communications in Win32"。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)
