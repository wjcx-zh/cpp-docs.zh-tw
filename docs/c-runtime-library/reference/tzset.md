---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: b2537a3bbfd2b5cec6bdf149c520aac7e3344b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362190"
---
# <a name="_tzset"></a>_tzset

設定時間環境變數。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
void _tzset( void );
```

## <a name="remarks"></a>備註

**_tzset**函數使用環境變數**TZ**的目前設定值分配給三個全域變數 **:_daylight、_timezone****_timezone**和 **_tzname**。 這些變數由[_ftime](ftime-ftime32-ftime64.md)和[本地時間](localtime-localtime32-localtime64.md)函數用於從協調的通用時間 (UTC) 到本地時間進行修正,以及根據系統時間計算 UTC[的時間](time-time32-time64.md)函數。 使用以下語法設定**TZ**環境變數:

> **設定 TZ_** **-**_tzn_ \[ **+**&#124;=*hh*\[**:**_mm_\[**:**_ss_= =*dzn*|

|參數|描述|
|-|-|
| *茨恩* | 三個字母的時區名稱，例如 PST (太平洋標準時間)。 您必須指定從本地時間到 UTC 的正確位移。 |
| *hh* | UTC 與本地時間之間的時間差異 (小時)。 正值可選用正號 (+)。 |
| *公釐* | 分鐘。 由冒號 **()** 與*hh*分離 。 |
| *ss* | 秒鐘。 由冒號 **()** 與*mm*分隔。 |
| *德茲* | 三個字母的日光節約時區例如 PDT。 如果夏令時在局部地區從未有效,則設置**TZ**而不為*dzn*的值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，假定使用美國的規則。 |

> [!NOTE]
> 要特別小心運算時間差異的正負號。 因為時間差異是從本地時間到 UTC (而不是從 UTC 到本地時間) 的位移，正負號可能與您直覺的預期相反。 早於 UTC 的時區，時間差異為負數；晚於 UTC 的時區，時間差異為正數。

例如,要將**TZ**環境變數設定為對應於德國的當前時區,請在命令列上輸入以下內容:

> **設定 TZ=GST-1GDT**

此命令會使用 GST 表示德國標準時間，並假設 UTC 比德國晚一小時 (也就是說，德國比 UTC 快一個小時) 以及德國會遵守日光節約時間。

如果未設置**TZ**值,**則_tzset**嘗試使用作業系統指定的時區資訊。 在 Windows 作業系統中，這項資訊是在 [控制台] 的 [日期/時間] 應用程式中指定。 如果 **_tzset**無法獲得此資訊,則默認情況下使用 PST8PDT,這表示太平洋時區。

根據**TZ**環境變數值,當調用 **_tzset**時,將以下值分配給 **_daylight、_timezone**和 **_tzname**的全域變數: **_timezone**

|全域變數|描述|預設值|
|---------------------|-----------------|-------------------|
|**_daylight**|如果在**TZ**設置中指定了夏令時區域,則非零值;否則,0。|1|
|**_timezone**|傳回本地時間與 UTC 之間的時差 (秒)。|28800 (28800 秒等於 8 小時)|
|**_tzname**[0]|**來自 TZ**環境變數的時區名稱的字串值;如果**TZ**尚未設置,則為空。|PST|
|**_tzname**[1]|夏令時區域的字串值;如果**從 TZ**環境變數中省略夏令時區域,則為空。|PDT|

上表中顯示**的_daylight**和 **_tzname**陣列的預設值對應於「PST8PDT」。。 如果從**TZ**環境變數中省略 DST 區域,**則_daylight**的值為 0,[並且 _ftime、gmtime](ftime-ftime32-ftime64.md)和[本地時間](localtime-localtime32-localtime64.md)函[gmtime](gmtime-gmtime32-gmtime64.md)數返回 0 的 DST 標誌。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_tzset**功能特定於 Microsoft。 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
