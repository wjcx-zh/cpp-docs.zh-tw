---
title: _heapwalk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapwalk
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d98260ce281bc8773f597dae5897afe4beee0bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403397"
---
# <a name="heapwalk"></a>_heapwalk

周遊堆積，並傳回下一個項目的相關資訊。

> [!IMPORTANT]
> 這個 API 除了偵錯組建之外，不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>參數

*entryinfo*<br/>
包含堆積資訊的緩衝區。

## <a name="return-value"></a>傳回值

**_heapwalk**傳回下列整數資訊清單常數在 Malloc.h 中定義的其中一個。

|傳回值|意義|
|-|-|
|**_HEAPBADBEGIN**| 找不到初始標頭資訊或其無效。|
|**_HEAPBADNODE**| 堆積已損毀或找到故障的節點。|
|**_HEAPBADPTR**| **_Pentry**欄位 **_HEAPINFO**堆積結構未包含有效的指標或*entryinfo*為 null 指標。|
|**_HEAPEND**| 已成功達到堆積的結尾。|
|**_HEAPEMPTY**| 堆積未初始化。|
|**_HEAPOK**| 沒有錯誤為止。*entryinfo*更新下一個堆積項目相關資訊。|

此外，如果發生錯誤， **_heapwalk**設定**errno**至**ENOSYS**。

## <a name="remarks"></a>備註

**_Heapwalk**函式可協助偵錯堆積相關的問題，在程式中。 函式逐步解說堆積，周遊呼叫，每一個項目，並傳回類型的結構指標 **_HEAPINFO** ，其中包含下一個堆積項目的相關資訊。 **_HEAPINFO** Malloc.h 中, 所定義的類型包含下列項目。

|欄位|意義|
|-|-|
|`int *_pentry`|堆積項目指標。|
|`size_t _size`|堆積項目大小。|
|`int _useflag`|表示堆積項目是否為使用中的旗標。|

呼叫 **_heapwalk**傳回 **_HEAPOK**儲存中的項目大小 **_size**欄位並設定 **_useflag**欄位設為 **_FREEENTRY**或 **_USEDENTRY** （兩者都是在 Malloc.h 中定義的常數）。 若要取得此堆積中的第一個項目相關資訊，請傳遞 **_heapwalk**指標 **_HEAPINFO**結構其 **_pentry**成員是**NULL**. 如果作業系統不支援 **_heapwalk**（例如 Windows 98），則函數會傳回 **_HEAPEND**並設定**errno**至**ENOSYS**.

這個函式會驗證其參數。 如果*entryinfo*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式 **_HEAPBADPTR**。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
