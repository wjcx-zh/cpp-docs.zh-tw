---
title: strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 573e89b7be9818ac45f70c7c614e3bf7869c95f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418155"
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime、wcsftime、_strftime_l、_wcsftime_l

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

*strDest*<br/>
輸出字串。

*maxsize*<br/>
大小*strDest*以字元為單位的緩衝區 (**char**或**wchar_t**)。

*格式*<br/>
格式控制字串。

*timeptr*<br/>
**tm**資料結構。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strftime**傳回的字元放在數*strDest*和**wcsftime**傳回對應的寬字元數目。

如果的總字元數，包括結束的 null 是多個*maxsize*，這兩個**strftime**和**wcsftime**傳回 0 到的內容*strDest*就無法確定。

中的字元數*strDest*等於常值中的字元數*格式*以及可能會加入至任何字元*格式*透過格式化程式碼。 字串的結束 Null 不會計入傳回值。

## <a name="remarks"></a>備註

**Strftime**和**wcsftime**函式格式**tm**時間值中的*timeptr*根據提供*格式*引數和存放區的緩衝區中的結果*strDest*。 最多*maxsize*字元會放在字串中。 如需說明中的欄位*timeptr*結構，請參閱[asctime](asctime-wasctime.md)。 **wcsftime**是寬字元等同於**strftime**; 其字串指標引數指向的寬字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果*strDest*，*格式*，或*timeptr*為 null 指標，或如果**tm**資料結構所定址*timeptr*無效 （例如，如果它包含超出範圍值的時間或日期），或如果*格式*字串包含無效的格式化程式碼、 無效參數處理常式會叫用，中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，函數會傳回 0 和集合允許執行**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*引數包含一個或多個程式碼，如下所示**printf**，格式化的代碼前面加上百分比符號 (**%**)。 不是以字元**%** 會複製到不變*strDest*。 **LC_TIME**類別目前的地區設定會影響輸出格式設定的**strftime**。 (如需有關**LC_TIME**，請參閱[setlocale](setlocale-wsetlocale.md)。)**Strftime**和**wcsftime**函式會使用目前設定的地區設定。 **_Strftime_l**和 **_wcsftime_l**這些函式版本是一樣的只不過它們會做為參數的地區設定並使用，而非目前已設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函式支援這些格式化程式碼：

|||
|-|-|
|程式碼|取代字串|
|**%a**|地區設定的縮寫的星期幾名稱|
|**%A**|完整的工作日名稱的地區設定|
|**%b**|縮寫的月份名稱的地區設定|
|**%B**|地區設定中的完整月份名稱|
|**%c**|適用於地區設定的日期和時間表示|
|**%C**|年份分成 100，而被截斷為整數，以十進位數字 (00−99)|
|**%d**|十進位數字 (01 – 31) 月份日期|
|**%D**|相當於 **%m/%d/%y**|
|**%e**|十進位數字 (1-31)，其中單一數字前置空格月份日期|
|**%F**|相當於 **%y-%m-%d**|
|**%g**|以十進位數字的 ISO 8601 週為基礎年份的最後 2 位數字 (00-99)|
|**%G**|以十進位數字的 ISO 8601 週為基礎年份|
|**%h**|縮寫的月份名稱 (相當於 **%b**)|
|**%H**|24 小時制的小時 (00-23)|
|**%I**|12 小時制 (01-12) 的|
|**%j**|以十進位數字 (001 到 366) 表示的年份的日期|
|**%m**|(01-12) 的十進位數字月份|
|**%M**|分鐘數的十進位數字 (00-59)|
|**%n**|新行字元 (**\n**)|
|**%p**|地區設定的 a.m./p.m. 12 小時制的指標|
|**%r**|地區設定的 12 小時制的時間|
|**%R**|相當於 **%h:%m%M**|
|**%S**|第二個十進位數字 (00-59)|
|**%t**|水平定位字元 (**\t**)|
|**%T**|相當於 **%h:%m: %s**，ISO 8601 時間格式|
|**%u**|ISO 8601 週間日的十進位數字 (1-7;星期一為 1）|
|**%U**|以十進位數字的年份的週次 (00-53)，其中第一個星期日是第 1 週的第一天|
|**%V**|ISO 8601 週數的十進位數字 (00-53)|
|**%w**|工作日的十進位數字 (0-6;星期日是 0）|
|**%W**|以十進位數字的年份的週次 (00-53)，其中第一個星期一是第 1 週的第一天|
|**%x**|日期表示地區設定|
|**%X**|地區設定的時間表示法|
|**%y**|不含世紀，為十進位數字的年份 (00-99)|
|**%Y**|含世紀的年份，以十進位數字表示|
|**%z**|從 UTC 的位移，採用 ISO 8601 格式。如果時區不知道任何字元|
|**%Z**|地區設定的時區名稱或時區縮寫，取決於登錄設定。如果時區不知道任何字元|
|**%%**|百分比符號|

在**printf**函式， **#** 旗標可能首碼格式的任何程式碼。 在此情況下，格式代碼的意義會變更如下。

|格式化程式碼|意義|
|-----------------|-------------|
|**%#a**， **%#A**， **%#b**， **%#B**， **%#g**， **%#G**， **%#h**， **%#n**， **%#p**， **%#t**， **%#u**， **%#w**， **%#X**， **%#z**， **%#Z**， **%#%**|**#** 會忽略旗標。|
|**%#c**|長時間的日期和時間表示法，適當的地區設定。 例如：「1995 年 3 月 14 日星期二 12:41:29」。|
|**%#x**|完整日期表示，適當的地區設定。 例如：「1995 年 3 月 14 日星期二」。|
|**%#d**， **%#D**， **%#e**， **%#F**， **%#H**， **%#I**， **%#j**， **%#m**， **%#M**， **%#r**， **%#R**， **%#S**， **%#T**， **%#U**， **%#V**， **%#W**， **%#y**， **%#Y**|移除前置的零或空格 （如果有的話）。|

所產生的 ISO 8601 週和每週為基礎的年份 **%V**， **%g**，和 **%G**，會使用以星期一，開始一週第 1 週所在包含年 1 月第 4 個，也就是第一週包含至少 4 天的年份的週次。 如果年份的第一個星期一第 2，3，或第 4 個，上述天屬於上述年的最後一週。 如這些發行日， **%V** 53，和會取代 **%g**和 **%G**取代上述年中的數字。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**和 **_wcsftime_l**函式是 Microsoft 專有。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [time](time-time32-time64.md) 的範例。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md) <br/>
[時間管理](../../c-runtime-library/time-management.md) <br/>
[字串操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
