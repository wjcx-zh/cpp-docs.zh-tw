---
title: outp、outpw、_outp、_outpw、_outpd
description: 描述 Microsoft C 執行時間程式庫（CRT）的已淘汰和已移除 outp、outpw、_outp、_outpw 和 _outpd 功能。
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
ms.openlocfilehash: 3d0342ae94276c7875bcb737b0d1a64aabafd235
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825924"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp、outpw、_outp、_outpw、_outpd

輸出，位於埠、`outp`位元組（， `_outp`）、單字（`outpw`， `_outpw`）或雙字組（`_outpd`）。

> [!IMPORTANT]
> 這些函式已被取代。 從 Visual Studio 2015 開始，它們無法在 CRT 中使用。
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```cpp
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

### <a name="parameters"></a>參數

*移植*\
連接埠號碼。

*databyte、dataword*\
輸出值。

## <a name="return-value"></a>傳回值

這些函式會傳回資料輸出。 不會傳回錯誤。

## <a name="remarks"></a>備註

`_outp`、 `_outpw`及 `_outpd` 函式會個別寫入一個位元組、一個字組及雙字組到指定的輸出連接埠。 *Port*引數可以是範圍 0-65535; 中的任何不帶正負號的整數。*databyte*可以是範圍 0-255 中的任何整數。和*dataword*可以是整數範圍內的任何值、不帶正負號的短整數，以及不帶正負號的長整數。

由於這些函式直接寫入 I/O 連接埠，因此無法用於使用者程式碼。 如需如何使用這些作業系統中之 I/O 連接埠的資訊，請前往 MSDN 搜尋 "Serial Communications in Win32"。

`outp`和`outpw`名稱是`_outp`和`_outpw`函式的舊版、已被取代的名稱。 如需詳細資訊，請參閱[POSIX 函數名稱](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>請參閱

[主控台和埠 i/o](../c-runtime-library/console-and-port-i-o.md)\
[sct.inp、inpw、_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)
