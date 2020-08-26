---
title: outp、outpw、_outp、_outpw _outpd
description: 描述 Microsoft C 執行時間程式庫 (CRT) 已淘汰和移除的 outp、outpw、_outp、_outpw 和 _outpd 函式。
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
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
- outp
- outpw
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
ms.openlocfilehash: c66710fe31b5a657a4976bea7f0aa52aac3e3825
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837082"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp、outpw、_outp、_outpw _outpd

在埠、位元組 (`outp` 、 `_outp`) 、單字 (`outpw` 、 `_outpw`) 或 double word `_outpd` () 輸出。

> [!IMPORTANT]
> 這些函式已被取代。 從 Visual Studio 2015 開始，它們無法在 CRT 中使用。
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```cpp
int _outp(
   unsigned short port,
   int data_byte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short data_word
);
unsigned long _outpd(
   unsigned short port,
   unsigned long data_word
);
```

### <a name="parameters"></a>參數

*港口*\
連接埠號碼。

*data_byte，data_word*\
輸出值。

## <a name="return-value"></a>傳回值

這些函式會傳回資料輸出。 不會傳回錯誤。

## <a name="remarks"></a>備註

`_outp`、 `_outpw`及 `_outpd` 函式會個別寫入一個位元組、一個字組及雙字組到指定的輸出連接埠。 *埠*引數可以是 0-65535 範圍內的任何不帶正負號的整數。 *data_byte* 可以是範圍 0-255 中的任何整數。 *data_word* 可以是整數範圍內的任何值、不帶正負號的短整數，以及不帶正負號的長整數。

因為這些函式會直接寫入 i/o 埠，所以無法在使用者模式的 Windows 程式碼中使用。

如需在 Windows 作業系統中使用 i/o 埠的詳細資訊，請參閱 [序列通訊](/previous-versions/ff802693(v=msdn.10))。

`outp`和 `outpw` 名稱是和函式的較舊、已被取代的名稱 `_outp` `_outpw` 。 如需詳細資訊，請參閱 [POSIX 函數名稱](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[主控台和埠 i/o](../c-runtime-library/console-and-port-i-o.md)\
[`inp`, `inpw`, `_inp`, `_inpw`, `_inpd`](../c-runtime-library/inp-inpw-inpd.md)
