---
title: _getch_nolock、_getwch_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getwch_nolock
- _getch_nolock
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getch_nolock
- getwch_nolock
- getch_nolock
- _getwch_nolock
- _gettch_nolock
- gettch_nolock
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- _getwch_nolock function
- _getch_nolock function
- getwch_nolock function
- _gettch_nolock function
- console, reading from
- getch_nolock function
- gettch_nolock function
ms.assetid: 9d248546-26ca-482c-b0c6-55812a987e83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e742dab8f77a4f66b77c7c9fdc4b45b5ace06be0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400700"
---
# <a name="getchnolock-getwchnolock"></a>_getch_nolock、_getwch_nolock

從無回應且未鎖定執行緒的主控台取得字元。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _getch_nolock( void );
wint_t _getwch_nolock( void );
```

## <a name="return-value"></a>傳回值

傳回讀取的字元。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_getch_nolock**和 **_getwch_nolock**相同 **_getch**和 **_getchw**不同之處在於它們不受干擾其他執行緒。 因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettch_nolock**|**_getch_nolock**|**_getch_nolock**|**_getwch_nolock**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_getch_nolock**|\<conio.h>|
|**_getwch_nolock**|\<conio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getch_nolock.c
// compile with: /c
// This program reads characters from
// the keyboard until it receives a 'Y' or 'y'.

#include <conio.h>
#include <ctype.h>

int main( void )
{
   int ch;

   _cputs( "Type 'Y' when finished typing keys: " );
   do
   {
      ch = _getch_nolock();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch_nolock( ch );
   _putch_nolock( '\r' );    // Carriage return
   _putch_nolock( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: Y
```

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getche、_getwche](getche-getwche.md)<br/>
[_cgets、_cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
