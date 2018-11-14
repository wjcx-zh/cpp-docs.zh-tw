---
title: _tzset
ms.date: 11/04/2016
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
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: 6312297e6daa9b4790674bd26d21812d5bee34c6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330251"
---
# <a name="tzset"></a>_tzset

設定時間環境變數。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
void _tzset( void );
```

## <a name="remarks"></a>備註

**_Tzset**函式會使用目前的環境變數設定**TZ**將值指派給三個全域變數： **_daylight**， **_timezone**，並 **_tzname**。 藉由使用這些變數[_ftime](ftime-ftime32-ftime64.md)並[localtime](localtime-localtime32-localtime64.md)函式來進行國際標準時間 (UTC) 的修正，本地時間、 to 和 by[時間](time-time32-time64.md)函式UTC 的系統時間計算。 使用下列語法來設定**TZ**環境變數：

> **設定 TZ =**_tzn_ \[ **+** &#124; **-**]*hh* \[ **:**_mm_\[**:**_ss_]] [*dzn*]

|參數|描述|
|-|-|
| *tzn* | 三個字母的時區名稱，例如 PST (太平洋標準時間)。 您必須指定從本地時間到 UTC 的正確位移。 |
| *hh* | UTC 與本地時間之間的時間差異 (小時)。 正值可選用正號 (+)。 |
| *mm* | 分鐘。 分開*hh*分號 (**:**)。 |
| *ss* | 秒鐘。 分開*公釐*分號 (**:**)。 |
| *dzn* | 三個字母的日光節約時區例如 PDT。 如果日光節約時間永遠不會作用中該位置，請設定**TZ**的值不*dzn*。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，假定使用美國的規則。 |

> [!NOTE]
> 要特別小心運算時間差異的正負號。 因為時間差異是從本地時間到 UTC (而不是從 UTC 到本地時間) 的位移，正負號可能與您直覺的預期相反。 早於 UTC 的時區，時間差異為負數；晚於 UTC 的時區，時間差異為正數。

例如，若要設定**TZ**環境變數，以對應至目前的時區，在德國，在命令列上輸入下列：

> **設定 TZ = GST 1GDT**

此命令會使用 GST 表示德國標準時間，並假設 UTC 比德國晚一小時 (也就是說，德國比 UTC 快一個小時) 以及德國會遵守日光節約時間。

如果**TZ**未設定值， **_tzset**嘗試使用作業系統所指定的時區資訊。 在 Windows 作業系統中，這項資訊是在 [控制台] 的 [日期/時間] 應用程式中指定。 如果 **_tzset**無法取得這項資訊，它會使用根據預設，這表示太平洋時區的 PST8PDT。

根據**TZ**環境變數的值，下列的值指派給全域變數 **_daylight**， **_timezone**，和 **_tzname**時 **_tzset**稱為：

|全域變數|描述|預設值|
|---------------------|-----------------|-------------------|
|**_daylight**|如果日光節約時間區域中指定的非零值**TZ**設定; 否則為 0。|1|
|**_timezone**|傳回本地時間與 UTC 之間的時差 (秒)。|28800 (28800 秒等於 8 小時)|
|**_tzname**[0]|時區名稱的字串值**TZ**環境變數; 如果空**TZ**尚未設定。|PST|
|**_tzname**[1]|字串值的日光節約時間區域中。如果日光節約時間區域中會省略空**TZ**環境變數。|PDT|

上表所示的預設值 **_daylight**並 **_tzname**陣列對應至"PST8PDT"。 如果從省略的 DST 區域，則**TZ**環境變數，值 **_daylight**為 0， [_ftime](ftime-ftime32-ftime64.md)， [gmtime](gmtime-gmtime32-gmtime64.md)，及[localtime](localtime-localtime32-localtime64.md)函式會傳回 0 代表其 DST 旗標。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_Tzset**是 Microsoft 特定的函式。 如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
