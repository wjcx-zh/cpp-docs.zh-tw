---
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: c5208c86484e1d9478f3879d91b32d57ba7c4a3a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912891"
---
# <a name="fflush"></a>fflush

排清資料流。

## <a name="syntax"></a>語法

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果已成功排清緩衝區， **fflush**會傳回0。 如果指定的資料流沒有任何緩衝區或僅開啟為唯讀，也會傳回值 0。 **EOF**的傳回值表示發生錯誤。

> [!NOTE]
> 如果**fflush**傳回**EOF**，資料可能會因為寫入失敗而遺失。 設定重大錯誤處理常式時，最安全的方式是使用**setvbuf**函數來關閉緩衝，或使用低層級 i/o 常式（例如 **_open**、 **_close**和 **_write** ，而不是資料流程 i/o 函式）。

## <a name="remarks"></a>備註

**Fflush**函數會排清資料流程*串流*。 如果資料流已在寫入模式中開啟，或已在更新模式中開啟而最後的作業是寫入，則資料流緩衝區的內容會寫入基礎檔案或裝置，而緩衝區會被捨棄。 如果資料流程是以讀取模式開啟，或資料流程沒有緩衝區，則呼叫**fflush**不會有任何作用，而且會保留任何緩衝區。 對**fflush**的呼叫會否定任何先前對資料流程的**ungetc**呼叫所造成的影響。 資料流在呼叫之後仍保持開啟。

如果*stream*為**Null**，則行為會與每個開啟的資料流程上的**fflush**呼叫相同。 所有在寫入模式中開啟的資料流，以及所有在更新模式中開啟且最後作業是寫入的資料流，都會排清。 呼叫對其他資料流不起作用。

緩衝區通常是由作業系統維護，這會決定資料自動寫入磁碟的最佳時機︰當緩衝區已滿、當資料流已關閉，或當程式正常結束但不關閉資料流。 執行階段程式庫的認可到磁碟功能可讓您確保將重大資料直接寫入至磁碟，而不是作業系統緩衝區。 不需要重新撰寫現有程式，即可連結程式的物件檔案與 COMMODE.OBJ 來啟用這項功能。 在產生的可執行檔中，呼叫 **_flushall**將所有緩衝區的內容寫入磁片。 只有 **_flushall**和**FFLUSH**會受到 commode.obj 的影響。

如需控制認可到磁碟功能的資訊，請參閱[資料流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

此函示鎖定呼叫執行緒，所以是安全執行緒。 如需非鎖定版本，請參閱 **_fflush_nolock**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
