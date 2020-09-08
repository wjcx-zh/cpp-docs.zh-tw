---
title: sct.inp、_inp、inpw、_inpw _inpd
description: 描述 Microsoft C 執行時間程式庫 (CRT) 已淘汰和移除的 sct.inp、_inp、inpw、_inpw 和 _inpd 函式。
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: aafcd633b2ee04c9ced1520d4ecd1520475d0fea
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556472"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>sct.inp、_inp、inpw、_inpw _inpd

輸入、埠、位元組 (`inp` 、 `_inp`) 、單字 (`inpw` 、 `_inpw`) 或 double word `_inpd` () 。

> [!IMPORTANT]
> 這些函式已被取代。 從 Visual Studio 2015 開始，它們無法在 CRT 中使用。
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>參數

*港口*\
I/O 連接埠號碼。

## <a name="return-value"></a>傳回值

這些函式會傳回從 `port`讀取而來的位元組、字組或雙字組。 不會傳回錯誤。

## <a name="remarks"></a>備註

`_inp`、 `_inpw`及 `_inpd` 函式會從指定的輸入連接埠讀取位元組、字組及雙字組。 輸入的值可以是 0 - 65535 之間任何不帶正負號的 short 整數。

由於這些函式直接從 I/O 連接埠讀取，因此無法用於使用者程式碼。

`inp`和 `inpw` 名稱是和函式的較舊、已被取代的名稱 `_inp` `_inpw` 。 如需詳細資訊，請參閱 [POSIX 函數名稱](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[主控台和埠 i/o](../c-runtime-library/console-and-port-i-o.md)\
[outp、outpw、_outp、_outpw _outpd](../c-runtime-library/outp-outpw-outpd.md)
