---
title: strftime、wcsftime、_strftime_l、_wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350008"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime、wcsftime、_strftime_l、_wcsftime_l

設定時間字串的格式。

## <a name="syntax"></a>語法

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*斯特德斯特*<br/>
輸出字串。

*最大大小*<br/>
*最串D*緩衝區的大小,以字元(**strs**或**wchar_t)** 度量。

*格式*<br/>
格式控制字串。

*timeptr*<br/>
**tm**數據結構。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strftime**傳回放置在*strD*中的字元數 **,wcsftime**返回相應的寬字元數。

如果字元總數(包括終止 null)大於*最大大小*,**則穩定時間和** **wcsftime**返回 0 和*strDest 的內容*都是不確定的。

*strDest*中的字元數等於*格式*中的字面字元數,以及可透過格式代碼添加到*格式*的任何字元數。 字串的結束 Null 不會計入傳回值。

## <a name="remarks"></a>備註

**strftime**與**wcsftime**函數根據提供的*格式*參數格式化*時間百分*值,並將結果儲存在緩衝區*strDest 中*。 **tm** 最多時 *,最大大小*字元放置在字串中。 有關*時間點*結構中的欄位的說明,請參閱[asctime](asctime-wasctime.md)。 **wcsftime**是寬字元等效於**時間;** 其字串指標參數指向寬字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果*strDest、**格式*或*timeptr*是空指標,或者如果*timeptr*解決的**tm**資料結構無效(例如,如果它包含時間或日期的出距範圍值),或者如果*格式*字串包含無效的格式代碼,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回 0 並將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*參數由一個或多個代碼組成;如**在 printf**中,格式代碼前面有**%** 百分號 ()。 不開頭**%** 的字元將複製到*stD。* 當前區域設置的**LC_TIME**類別會影響**穩點時間的**輸出格式。 (有關**LC_TIME**的詳細資訊,請參閱[設定區域設定](setlocale-wsetlocale.md)。)**定時**和**wcsftime**函數使用當前設置區域設置。 這些函數**的_strftime_l**和 **_wcsftime_l**版本相同,只是它們將區域設置作為參數並使用該參數而不是當前設置的區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**時間**函數支援以下格式碼:

|||
|-|-|
|程式碼|取代字串|
|**%a**|區域設定的縮寫工作日名稱|
|**%A**|地區設定的完整工作日名稱|
|**%b**|地區設定的縮寫月份名稱|
|**%B**|地區設定的完整月名稱|
|**%c**|適用於地區設定的日期和時間表示|
|**%C**|年份除以 100,並截斷為整數,作為小數 (00+99)|
|**%d**|每月的天數為小數 (01 - 31)|
|**%D**|等效於 **%d/%d/%y**|
|**%e**|每月的一天作為小數(1 - 31),其中位元元元前面有空格|
|**%F**|等效於 **%Y-%m-%d**|
|**%g**|ISO 8601 基於周的年份的最後 2 位元數字為小數 (00 - 99)|
|**%G**|ISO 8601 基於周的年份作為小數|
|**%h**|縮寫月份名稱 (等效於 **%b)**|
|**%H**|24 小時格式的小時(00 - 23)|
|**%I**|12 小時格式的小時 (01 - 12)|
|**%j**|一年中的某一天作為小數 (001 - 366)|
|**%m**|為小數數的月份 (01 - 12)|
|**%M**|分鐘作為小數 (00 - 59)|
|**%n**|新線字元 (**\n**)|
|**%p**|區域設定的 A.M./P.M. 12 小時制的指標|
|**%r**|區域設定的 12 小時時鐘時間|
|**%R**|等效於 **%H:%M**|
|**%S**|第二位為小數 (00 - 59)|
|**%t**|水平選項卡字元 (**\t**)|
|**%T**|等效於 **%H:%M:%S,ISO**8601 時間格式|
|**%u**|ISO 8601 工作日作為小數(1 - 7;星期一是 1)|
|**%U**|年份的周數為小數(00 - 53),其中第一個星期日是第 1 周的第一天|
|**%V**|ISO 8601 周數作為小數 (00 - 53)|
|**%w**|工作日作為小數(0 - 6;周日是 0)|
|**%W**|年份的周數為小數(00 - 53),其中第一個星期一是第 1 周的第一天|
|**%x**|區域設定的日期表示|
|**%X**|區域設定的時間表示|
|**%y**|無世紀年份,作為十進位數位 (00 - 99)|
|**%Y**|含世紀的年份，以十進位數字表示|
|**%z**|ISO 8601 格式的 UTC 偏移量;如果時區未知,則沒有字元|
|**%Z**|區域設置的時區名稱或時區縮寫,具體取決於註冊表設置;如果時區未知,則沒有字元|
|**%%**|百分比符號|

與**printf**函數**#** 中一樣,標誌可以對任何格式代碼進行前綴。 在此情況下，格式代碼的意義會變更如下。

|格式化程式碼|意義|
|-----------------|-------------|
|**%#a,** **%#A**, **%#b**, **%#B**, **%#g**% **#G**% **#h**, **%#n**, **%#p**,**百分之#t**、**百分之#u**、 **%#w**、 **#X**% **#z**、**百分之#Z**、**%#%**|**#** 將忽略標誌。|
|**%#c**|長日期和時間表示形式,適合區域設置。 例如：「1995 年 3 月 14 日星期二 12:41:29」。|
|**%#x**|長日期表示形式,適合區域設置。 例如：「1995 年 3 月 14 日星期二」。|
|**百#d**、 **#D %** **#e**、 **%#F,** **#H**% **#I**、 **%#j、** **#m** **%**#M, **#r**% **#R**、 **%#S**、 **%#T、** **#U、****百#V**、 **#W**% #W 、 **%#y**、 **%#Y**|刪除前導零或空格(如果有)。|

由 **%V、%g**和 **%G****%g**生產的 ISO 8601 周和基於一週的年份使用從星期一開始的一周,其中第 1 周是包含 1 月 4 日的一周,即包含一年中至少四天的第一周。 如果一年的第一個星期一是第 2、3 或第 4 個,則前幾天是上一年最後一周的一部分。 在那些日子裡 **,%V**替換為 53,%g 和 **%G**都取代 **%g**為上一年的數位。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_strftime_l**和 **_wcsftime_l**功能特定於 Microsoft。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [time](time-time32-time64.md) 的範例。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md) <br/>
[時間管理](../../c-runtime-library/time-management.md) <br/>
[字串動作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
