---
title: _heapwalk
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: cc2a49d9032746cc6c82c9dc401fc96baabbe2e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331684"
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

**_heapwalk**會傳回在 Malloc.h 中定義下列整數資訊清單常數之一。

|傳回值|意義|
|-|-|
|**_HEAPBADBEGIN**| 找不到初始標頭資訊或其無效。|
|**_HEAPBADNODE**| 堆積已損毀或找到故障的節點。|
|**_HEAPBADPTR**| **_Heapinfo**欄位 **_HEAPINFO**堆積結構不包含有效的指標或*entryinfo*為 null 指標。|
|**_HEAPEND**| 已成功達到堆積的結尾。|
|**_HEAPEMPTY**| 堆積未初始化。|
|**_HEAPOK**| 到目前為止，沒有錯誤*entryinfo*會更新下一個堆積項目的相關資訊。|

此外，如果發生錯誤時， **_heapwalk**設定**errno**來**ENOSYS**。

## <a name="remarks"></a>備註

**_Heapwalk**函式可協助偵錯程式中的堆積相關問題。 函式查核堆積，周遊一個項目，每一呼叫和傳回類型的結構的指標 **_HEAPINFO** ，其中包含下一個堆積項目的相關資訊。 **_HEAPINFO** Malloc.h 中定義的類型包含下列項目。

|欄位|意義|
|-|-|
|`int *_pentry`|堆積項目指標。|
|`size_t _size`|堆積項目大小。|
|`int _useflag`|表示堆積項目是否為使用中的旗標。|

呼叫 **_heapwalk**會傳回 **_HEAPOK**存放區中的項目大小**大小) (_s**欄位和集 **_heapinfo**欄位設為其中一個 **_FREEENTRY**或是 **_USEDENTRY** （兩者都是 Malloc.h 中定義的常數）。 若要取得此堆積中的第一個項目相關資訊，請傳遞 **_heapwalk**指標 **_HEAPINFO**結構，其 **_heapinfo**成員是**NULL**. 如果作業系統不支援 **_heapwalk**（例如 Windows 98），則函數會傳回 **_HEAPEND**並設定**errno**至**ENOSYS**.

這個函式會驗證其參數。 如果*entryinfo*為 null 指標，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回 **_HEAPBADPTR**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
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
