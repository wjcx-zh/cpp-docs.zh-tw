---
title: _CrtSetDbgFlag | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetDbgFlag
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
apitype: DLLExport
f1_keywords:
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d6ed7ff3e28028e3e4b46055e51c32037b0b5a15
ms.lasthandoff: 02/24/2017

---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag
擷取或修改 **_crtDbgFlag** 旗標的狀態，以控制偵錯堆積管理員的配置行為 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _CrtSetDbgFlag(   
   int newFlag   
);  
```  
  
#### <a name="parameters"></a>參數  
 `newFlag`  
 **_crtDbgFlag** 的新狀態。  
  
## <a name="return-value"></a>傳回值  
 傳回 **_crtDbgFlag** 先前的狀態。  
  
## <a name="remarks"></a>備註  
 `_CrtSetDbgFlag` 函式可讓應用程式透過修改 **_crtDbgFlag** 旗標的位元欄位，進而控制偵錯堆積管理員如何追蹤記憶體配置。 應用程式可透過設定位元 (開啟)，指示偵錯堆積管理員執行特定偵錯作業，包含在應用程式結束時檢查記憶體遺漏並在發現任何問題時進行回報，以及藉由指定已釋放的記憶體區塊應保留在堆積的連結清單中來模擬低記憶體的情況，還有在每次配置要求時透過檢查每個記憶體區塊來驗證堆積的完整性。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetDbgFlag` 的呼叫。  
  
 下表列出 **_crtDbgFlag** 的位元欄位，並描述它們的行為。 因為設定位元會導致增加診斷輸出，並降低程式執行速度，所以預設不會設定這些位元 (關閉)。 如需這些位元欄位的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。  
  
|位元欄位|預設|描述|  
|---------------|-------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|ON|ON：啟用偵錯堆積配置，並使用記憶體區塊類型識別項，例如 `_CLIENT_BLOCK`。 OFF：新增配置至堆積的連結清單，但將區塊類型設定為 **_IGNORE_BLOCK**。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|  
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|ON：在每次配置及解除配置要求時，呼叫 [_CrtCheckMemory](../../c-runtime-library/reference/crtcheckmemory.md)。 OFF：必須明確地呼叫 `_CrtCheckMemory`。<br /><br /> 堆積頻率檢查巨集會在設定此旗標時沒有效果。|  
|`_CRTDBG_CHECK_CRT_DF`|OFF|ON：在遺漏檢查及記憶體狀態差異作業中包含 `_CRT_BLOCK` 類型。 OFF：這些作業會忽略由執行階段程式庫內部所使用的記憶體。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|ON：將釋放的記憶體區塊保留在堆積的連結清單中，指派 **_FREE_BLOCK** 類型給這些記憶體區塊，並將它們填入位元組值 0xDD。 OFF：不要將釋放的記憶體區塊保留在堆積的連結清單中。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|  
|`_CRTDBG_LEAK_CHECK_DF`|OFF|ON：在程式結束時，透過呼叫 [_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) 執行自動流失檢查，並在應用程式失敗時產生錯誤報表，以釋放其配置的所有記憶體。 OFF：不要在應用程式結束時自動執行遺漏檢查。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|  
  
 **堆積檢查頻率巨集**  
  
 您可以根據呼叫 `malloc`、`realloc`、**free** 及 `_msize` 的次數，指定 C 執行階段程式庫執行偵錯堆積驗證 (`_CrtCheckMemory`) 的頻率。  
  
 然後 `_CrtSetDbgFlag` 會檢查 `newFlag` 參數的上層 16 位元以取得值。 指定的值是 `_CrtCheckMemory` 呼叫之間，呼叫 `malloc`、`realloc`、**free** 及 `_msize` 的次數。 針對此用途有四個預先定義的巨集。  
  
|巨集|_CrtCheckMemory 呼叫之間，呼叫 malloc、realloc、free 及 _msize 的次數|  
|-----------|------------------------------------------------------------------------------------------|  
|_CRTDBG_CHECK_EVERY_16_DF|16|  
|_CRTDBG_CHECK_EVERY_128_DF|128|  
|_CRTDBG_CHECK_EVERY_1024_DF|1024|  
|_CRTDBG_CHECK_DEFAULT_DF|0 (根據預設沒有檢查任何堆積)|  
  
 根據預設，會在您每 1,024 次呼叫 `malloc`、`realloc`、**free** 及 `_msize` 時，呼叫 `_CrtCheckMemory`。  
  
 例如，您可以使用下列程式碼，指定在 16 次 `malloc`、`realloc`、**free** 及 `_msize` 作業後，進行堆積檢查：  
  
```  
#include <crtdbg.h>  
int main( )  
{  
int tmp;  
  
// Get the current bits  
tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
  
// Clear the upper 16 bits and OR in the desired freqency  
tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;  
  
// Set the new bits  
_CrtSetDbgFlag(tmp);  
}  
```  
  
 指定 _CRTDBG_CHECK_ALWAYS_DF 時，會忽略 `newFlag` 參數的上層 16 位元。 在此情況中，會在您每次呼叫 `malloc`、`realloc`、**free** 及 `_msize` 時，呼叫 `_CrtCheckMemory`。  
  
 `newFlag` 是要套用至 **_crtDbgFlag** 的新狀態，並且是由每個位元欄位的值組合而成。  
  
### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>變更一個或多個位元欄位並建立旗標的新狀態  
  
1.  使用等於 `_CRTDBG_REPORT_FLAG` 的`newFlag` 呼叫 `_CrtSetDbgFlag`，以取得目前 **_crtDbgFlag** 狀態，並將傳回的值儲存在暫存變數中。  
  
2.  使用 `OR` 將暫存變數和對應的位元遮罩 (以資訊清單常數表示於應用程式程式碼中) 結合，以開啟任何位元。  
  
3.  使用 **AND** 將變數與適當位元遮罩的位元 **NOT** 結合，以關閉其他位元。  
  
4.  使用等於儲存在暫存變數中的值的 `newFlag` 呼叫 `_CrtSetDbgFlag`，以設定 **_crtDbgFlag** 的新狀態。  
  
 下列程式碼示範如何透過使釋放的記憶體區塊保留在堆積的連結清單中，來模擬低記憶體情況，以及防止在每次配置要求時呼叫 `_CrtCheckMemory`。  
  
```  
// Get the current state of the flag  
// and store it in a temporary variable  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn On (OR) - Keep freed memory blocks in the  
// heap's linked list and mark them as freed  
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;  
  
// Turn Off (AND) - prevent _CrtCheckMemory from  
// being called at every allocation request  
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;  
  
// Set the new state for the flag  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 如需記憶體管理及偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
 若要使用 `_CrtSetDbgFlag` 函式停用旗標，您應使用 **AND** 將變數與位元遮罩的位元 **NOT** 結合。  
  
 如果 `newFlag` 不是有效值，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `_crtDbgFlag` 先前的狀態。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_CrtSetDbgFlag`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_crtsetdflag.c  
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug  
/*  
 * This program concentrates on allocating and freeing memory  
 * blocks to test the functionality of the _crtDbgFlag flag..  
 */  
  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( )  
{  
        char *p1, *p2;  
        int tmpDbgFlag;  
  
        _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );  
        _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );  
        /*  
         * Set the debug-heap flag to keep freed blocks in the  
         * heap's linked list - This will allow us to catch any  
         * inadvertent use of freed memory  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;  
        tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Allocate 2 memory blocks and store a string in each  
         */  
        p1 = malloc( 34 );  
        p2 = malloc( 38 );  
        strcpy_s( p1, 34, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 38, "p2 points to a Client allocation block" );  
  
        /*  
         * Free both memory blocks  
         */  
        free( p2 );  
        free( p1 );  
  
        /*  
         * Set the debug-heap flag to no longer keep freed blocks in the  
         * heap's linked list and turn on Debug type allocations (CLIENT)  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;  
        tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Explicitly call _malloc_dbg to obtain the filename and   
         * line number of our allocation request and also so we can   
         * allocate CLIENT type blocks specifically for tracking  
         */  
        p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );  
        p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );  
        strcpy_s( p1, 40, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 40, "p2 points to a Client allocation block" );  
  
        /*  
         * _free_dbg must be called to free the CLIENT block  
         */  
        _free_dbg( p2, _CLIENT_BLOCK );  
        free( p1 );  
  
        /*  
         * Allocate p1 again and then exit - this will leave unfreed  
         * memory on the heap  
         */  
        p1 = malloc( 10 );  
}  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtCheckMemory](../../c-runtime-library/reference/crtcheckmemory.md)
