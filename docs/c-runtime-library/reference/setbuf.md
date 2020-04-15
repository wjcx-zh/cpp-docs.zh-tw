---
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
api_location:
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: f96cffb8770cda78ebff8d873b441ddc288bc41f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332070"
---
# <a name="setbuf"></a>setbuf

控制資料流緩衝處理。 已取代此函式；請改用 [setvbuf](setvbuf.md)。

## <a name="syntax"></a>語法

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

*緩衝區*<br/>
使用者配置的緩衝區。

## <a name="remarks"></a>備註

**setbuf**函數控制*流的*緩衝。 *串*流參數必須引用尚未讀取或寫入的打開檔。 如果*緩衝區*參數為**NULL,** 則流將取消緩衝。 如果不是,緩衝區必須指向長度**為 BUFSIZ**的字元陣列,其中**BUFSIZ**是 STDIO 中定義的緩衝區大小。H。 使用者指定的緩衝區 (而非指定資料流的預設系統配置緩衝區) 用於 I/O 緩衝處理。 預設情況下,**斯特值流**未緩衝,但您可以使用**setbuf**將緩衝區分配給**更穩。**

**setbuf**已被[setvbuf](setvbuf.md)替換,這是新代碼的首選例程。 與**setvbuf**不同 **,setbuf**無法報告錯誤。 **setvbuf**還允許您控制緩衝模式和緩衝區大小。 **setbuf**存在是為了與現有代碼相容。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
