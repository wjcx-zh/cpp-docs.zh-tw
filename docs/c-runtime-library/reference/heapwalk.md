---
title: "_heapwalk | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapwalk"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "heapwalk"
  - "_heapwalk"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapwalk 函式"
  - "偵錯 [CRT], 堆積相關的問題"
  - "heapwalk 函式"
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _heapwalk
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

周遊堆積並傳回用於下一個項目的相關資訊。  
  
> [!IMPORTANT]
>  這個應用程式開發介面無法在 Windows 執行階段執行的應用程式，除了在偵錯組建。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### 參數  
 `entryinfo`  
 包含堆積資訊的緩衝區。  
  
## 傳回值  
 `_heapwalk` 傳回在 Malloc.h 定義的下列整數資訊清單常數。  
  
 `_HEAPBADBEGIN`  
 初始標頭資訊無效或找不到。  
  
 `_HEAPBADNODE`  
 堆積損毀的或找到的錯誤節點。  
  
 `_HEAPBADPTR`  
 `_HEAPINFO` 結構的`_pentry` 欄位未包含輸入堆積有效的指標或 `entryinfo` 為 null 指標。  
  
 `_HEAPEND`  
 已成功到達的堆積的結尾。  
  
 `_HEAPEMPTY`  
 堆積尚未初始化  
  
 `_HEAPOK`  
 到目前為止沒有錯誤； `entryinfo` 更新以下堆積輸入的資訊。  
  
 此外，如果發生錯誤，則為 `_heapwalk` ，將 `errno` 設為 `ENOSYS`。  
  
## 備註  
 `_heapwalk` 函式可協助偵錯程式中的堆積相關的問題。  函式透過堆積查核，周遊呼叫每一個項目，並將指標傳回包含下堆積輸入的資訊型別 `_HEAPINFO` 的結構。  `_HEAPINFO` 型別，定義在 Malloc.h，包含下列項目。  
  
 `int *_pentry`  
 堆積輸入指標。  
  
 `size_t _size`  
 堆積輸入的大小。  
  
 `int _useflag`  
 旗標表示堆積輸入是否正在使用中。  
  
 對 `_heapwalk` 的呼叫是在 `_size` 中傳回 `_HEAPOK` 存放區之輸入的大小並將 `_useflag` 欄位設為 `_FREEENTRY` 或 `_USEDENTRY` \(都在 Malloc.h 定義的常數\)。  取得在堆積第一個項目的這個資訊，傳遞 `_heapwalk` 指標到 `_pentry` 成員為 `NULL`的 `_HEAPINFO` 結構。  如果作業系統不支援 `_heapwalk`\(例如， Windows 98\)，則函式會傳回 `_HEAPEND` 且將 `errno` 設為 `ENOSYS`。  
  
 這個函式會驗證其參數。  如果 `entryinfo` 如  [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述為 null 指標，則叫用無效參數處理常式。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `_HEAPBADPTR`。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_heapwalk`|\<malloc.h\>|\<errno.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
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
  
  **USED block at 00310650 of size 0100**  
 **USED block at 00310758 of size 0800**  
 **USED block at 00310F60 of size 0080**  
 **FREE block at 00310FF0 of size 0398**  
 **USED block at 00311390 of size 000D**  
 **USED block at 003113A8 of size 00B4**  
 **USED block at 00311468 of size 0034**  
 **USED block at 003114A8 of size 0039**  
**...**  
 **USED block at 00312228 of size 0010**  
 **USED block at 00312240 of size 1000**  
 **FREE block at 00313250 of size 1DB0**  
**OK \- end of heap**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../../c-runtime-library/heapset.md)