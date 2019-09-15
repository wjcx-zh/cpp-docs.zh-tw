---
title: _heapwalk
ms.date: 11/04/2016
api_name:
- _heapwalk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: 8dc7ee9335f227bde93a414748ff70b165c44f8d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954782"
---
# <a name="_heapwalk"></a>_heapwalk

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

**_heapwalk**會傳回在 Malloc. h 中定義的下列其中一個整數資訊清單常數。

|傳回值|意義|
|-|-|
|**_HEAPBADBEGIN**| 找不到初始標頭資訊或其無效。|
|**_HEAPBADNODE**| 堆積已損毀或找到故障的節點。|
|**_HEAPBADPTR**| **_HEAPINFO**結構的 **_pentry**欄位在堆積中不包含有效的指標，或*entryinfo*為 null 指標。|
|**_HEAPEND**| 已成功達到堆積的結尾。|
|**_HEAPEMPTY**| 堆積未初始化。|
|**_HEAPOK**| 目前沒有任何錯誤;*entryinfo*會使用下一個堆積專案的相關資訊進行更新。|

此外，如果發生錯誤， **_heapwalk**會將**Errno**設定為**ENOSYS**。

## <a name="remarks"></a>備註

**_Heapwalk**函數可協助在程式中偵測堆積相關的問題。 函式會逐步解說堆積、每次呼叫的一個專案，並傳回 **_HEAPINFO**類型結構的指標，其中包含下一個堆積專案的相關資訊。 **_HEAPINFO**類型（定義于 Malloc. h 中）包含下列元素。

|欄位|意義|
|-|-|
|`int *_pentry`|堆積項目指標。|
|`size_t _size`|堆積項目大小。|
|`int _useflag`|表示堆積項目是否為使用中的旗標。|

呼叫會傳回 **_HEAPOK**的 **_heapwalk**會在 **_size**欄位中儲存專案的大小，並將 **_useflag**欄位設定為 **_FREEENTRY**或 **_USEDENTRY** （這兩者都是在 Malloc. h 中定義的常數）。 若要取得有關堆積中第一個專案的這項資訊，請將指標傳遞給 **_heapwalk** ，**其 _Pentry**成員為**Null**的 **_HEAPINFO**結構。 如果作業系統不支援 **_heapwalk**（例如，Windows 98），此函式會傳回 **_HEAPEND** ，並將**errno**設定為**ENOSYS**。

這個函式會驗證其參數。 如果*entryinfo*為 null 指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回 **_HEAPBADPTR**。

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
