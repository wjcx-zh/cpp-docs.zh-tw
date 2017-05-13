---
title: _heapwalk | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 936ca2f3f4e4f2fb57dd730f5a58927d08d6207f
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="heapwalk"></a>_heapwalk
周遊堆積，並傳回下一個項目的相關資訊。  
  
> [!IMPORTANT]
>  這個 API 除了偵錯組建之外，不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### <a name="parameters"></a>參數  
 `entryinfo`  
 包含堆積資訊的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 `_heapwalk` 會傳回下列在 Malloc.h 中定義的整數資訊清單常數之一。  
  
 `_HEAPBADBEGIN`  
 找不到初始標頭資訊或其無效。  
  
 `_HEAPBADNODE`  
 堆積已損毀或找到故障的節點。  
  
 `_HEAPBADPTR`  
`_HEAPINFO` 結構的  `_pentry` 欄位進入堆積不包含有效的指標或 `entryinfo` 為 Null 指標。  
  
 `_HEAPEND`  
 已成功達到堆積的結尾。  
  
 `_HEAPEMPTY`  
 堆積未初始化。  
  
 `_HEAPOK`  
 到目前為止，沒有錯誤；已使用下一個堆積項目的相關資訊更新 `entryinfo`。  
  
 此外，若是發生錯誤，`_heapwalk` 會將 `errno` 設為 `ENOSYS`。  
  
## <a name="remarks"></a>備註  
 `_heapwalk` 函式可協助程式中堆積相關問題的偵錯。 函式會查核堆積，每次呼叫周遊一個項目，並將指標傳回至包含下一個堆積項目的 `_HEAPINFO` 類型結構。 Malloc.h 中定義的 `_HEAPINFO` 類型包含下列項目。  
  
 `int *_pentry`  
 堆積項目指標。  
  
 `size_t _size`  
 堆積項目大小。  
  
 `int _useflag`  
 表示堆積項目是否為使用中的旗標。  
  
 呼叫 `_heapwalk` 並傳回 `_HEAPOK` 時，項目大小會被儲存在 `_size` 欄位，並將 `_useflag` 欄位設定為 `_FREEENTRY` 或 `_USEDENTRY` 其中之一 (兩者都是 Malloc.h 中定義的常數)。 若要取得此堆積中第一個項目的資訊，請將 `_heapwalk` 指標傳遞至 `_pentry` 成員為 `NULL` 的`_HEAPINFO` 結構。 如果作業系統不支援 `_heapwalk` (例如，Windows 98)，函式會傳回 `_HEAPEND`，並將 `errno` 設定為 `ENOSYS`。  
  
 這個函式會驗證其參數。 如果 `entryinfo` 為 Null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `_HEAPBADPTR`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_heapwalk`|\<malloc.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
        printf("%6s block at %Fp of size %4.4X\n",  
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
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)
