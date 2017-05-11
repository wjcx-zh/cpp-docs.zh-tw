---
title: _tzset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _tzset
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tzset
dev_langs:
- C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 669b7d41234c21c3fb4e9a1a28f6b8d1a33c036b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="tzset"></a>_tzset
設定時間環境變數。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱                  [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
void _tzset( void );  
```  
  
## <a name="remarks"></a>備註  
 `_tzset` 函式會使用環境變數 `TZ` 目前的設定，將值指派給下列三個全域變數： `_daylight`、 `_timezone`和 `_tzname`。 [_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函式會使用這些變數來進行國際標準時間 (UTC) 到本地時間的更正， `time` 函式則會用這些變數進行系統時間到 UTC 的計算。 請使用下列語法來設定 `TZ` 環境變數：  
  
 `set` `TZ`=`tzn`[+ &#124; -]`hh`[`:``mm`[`:``ss`] ][`dzn`]  
  
 `tzn`  
 三個字母的時區名稱，例如 PST (太平洋標準時間)。 您必須指定從本地時間到 UTC 的正確位移。  
  
 `hh`  
 UTC 與本地時間之間的時間差異 (小時)。 正值可選用正號 (+)。  
  
 `mm`  
 分鐘。 以冒號 ( `hh` ) 分隔`:`。  
  
 `ss`  
 秒鐘。 以冒號 ( `mm` ) 分隔`:`。  
  
 `dzn`  
 三個字母的日光節約時區例如 PDT。 如果日光節約時間永遠不會在該位置生效，設定 `TZ` 時就不需設定 `dzn`的值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，假定使用美國的規則。  
  
> [!NOTE]
>  要特別小心運算時間差異的正負號。 因為時間差異是從本地時間到 UTC (而不是從 UTC 到本地時間) 的位移，正負號可能與您直覺的預期相反。 早於 UTC 的時區，時間差異為負數；晚於 UTC 的時區，時間差異為正數。  
  
 例如，若要設定 `TZ` 環境變數以對應至德國目前的時區，請輸入下列命令列：  
  
```  
set TZ=GST-1GDT  
```  
  
 此命令會使用 GST 表示德國標準時間，並假設 UTC 比德國晚一小時 (也就是說，德國比 UTC 快一個小時) 以及德國會遵守日光節約時間。  
  
 如果`TZ`未設定值，`_tzset`嘗試使用作業系統所指定的時區資訊。 在 Windows 作業系統中，這項資訊是在 [控制台] 的 [日期/時間] 應用程式中指定。 如果 `_tzset` 無法取得這項資訊，它會使用預設值 PST8PDT，表示太平洋時區。  
  
 根據 `TZ` 環境變數的值，在呼叫 `_daylight`時會將下列值指派給全域變數 `_timezone`、 `_tzname` 和 `_tzset` ：  
  
|全域變數|描述|預設值|  
|---------------------|-----------------|-------------------|  
|`_daylight`|如果 `TZ` 設定中指定日光節約時區為非零值 ；否則為 0。|1|  
|`_timezone`|傳回本地時間與 UTC 之間的時差 (秒)。|28800 (28800 秒等於 8 小時)|  
|`_tzname`[0]|來自 `TZ` 環境變數的時區名稱字串值；如果 `TZ` 尚未設定，則為空白。|PST|  
|`_tzname`[1]|日光節約時區的字串值；如果要省略 `TZ` 環境變數的日光節約時區，則為空白。|PDT|  
  
 上表中顯示的 `_daylight` 和 `_tzname` 陣列預設值會對應至 "PST8PDT"。 如果會省略 `TZ` 環境變數的 DST 區域， `_daylight` 的值為 0，且 `_ftime`、 `gmtime`和 `localtime` 函式會傳回 0 代表其 DST 旗標。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_tzset`|\<time.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_tzset.cpp  
// This program uses _tzset to set the global variables  
// named _daylight, _timezone, and _tzname. Since TZ is  
// not being explicitly set, it uses the system time.  
  
#include <time.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    _tzset();  
    int daylight;  
    _get_daylight( &daylight );  
    printf( "_daylight = %d\n", daylight );  
    long timezone;  
    _get_timezone( &timezone );  
    printf( "_timezone = %ld\n", timezone );  
    size_t s;  
    char tzname[100];  
    _get_tzname( &s, tzname, sizeof(tzname), 0 );  
    printf( "_tzname[0] = %s\n", tzname );  
    exit( 0 );  
}  
```  
  
```Output  
_daylight = 1  
_timezone = 28800  
_tzname[0] = Pacific Standard Time  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)
