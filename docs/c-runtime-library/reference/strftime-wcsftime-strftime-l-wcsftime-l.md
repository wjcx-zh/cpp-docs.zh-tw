---
title: strftime、wcsftime、_strftime_l、_wcsftime_l
ms.date: 03/22/2018
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
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353835"
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
大小*strDest*緩衝區，以字元為單位測量 (**char**或是**wchar_t**)。

*格式*<br/>
格式控制字串。

*timeptr*<br/>
**tm**資料結構。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strftime**傳回的字元放在數*strDest*並**wcsftime**傳回對應的寬字元數目。

如果總數目的字元，包括終止的 null，以上*maxsize*，這兩個**strftime**並**wcsftime**傳回 0 到的內容*strDest*就無法確定。

中的字元數*strDest*等於常值中的字元數*格式*以及可能會加入任何字元*格式*透過格式代碼。 字串的結束 Null 不會計入傳回值。

## <a name="remarks"></a>備註

**Strftime**並**wcsftime**函式格式**tm**時間值中的*timeptr*根據所提供*格式*引數並將結果儲存在緩衝區*strDest*。 最多*maxsize*字元會放在字串中。 如需中的欄位的說明*timeptr*結構，請參閱[asctime](asctime-wasctime.md)。 **wcsftime**是寬字元等於**strftime**; 其字串指標引數指向的寬字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果*strDest*，*格式*，或*timeptr*為 null 指標，或如果**tm**所定址的資料結構*timeptr*無效 （例如，如果它包含超出範圍的值時間或日期），或者如果*格式*字串包含無效的格式代碼、 無效參數處理常式會叫用，述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，則函式會傳回 0 並集允許執行**errno**要**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*引數包含一或多個程式碼，如下所示**printf**，格式代碼前會加上百分比符號 ( **%** )。 不是以開頭的字元 **%** 會複製不變，可*strDest*。 **LC_TIME**類別的目前地區設定會影響的輸出格式**strftime**。 (如需詳細資訊**LC_TIME**，請參閱[setlocale](setlocale-wsetlocale.md)。)**Strftime**並**wcsftime**函式會使用目前設定的地區設定。 **_Strftime_l**並 **_wcsftime_l**這些函式的版本完全相同，不同之處在於做為參數的地區設定，並使用，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函式支援這些格式化程式碼：

|||
|-|-|
|程式碼|取代字串|
|**%a**|地區設定中的縮寫的星期幾名稱|
|**%A**|地區設定中的完整的工作日名稱|
|**%b**|地區設定中的縮寫的月份名稱|
|**%B**|地區設定中的完整月份名稱|
|**%c**|適用於地區設定的日期和時間表示|
|**%C**|除以 100 年，並截斷為整數，以十進位數字 (00−99)|
|**%d**|一天的月份，以十進位數字 (01 – 31)|
|**%D**|相當於 **%m/%d/%y**|
|**%e**|十進位數字 (1 – 31)，其中單一數字月份的天數會加上空格|
|**%F**|相當於 **%y-%m-%d**|
|**%g**|以十進位數字的 ISO 8601 週為基礎年份的最後 2 個位數字 (00-99)|
|**%G**|以十進位數字的 ISO 8601 週為基礎年份|
|**%h**|縮寫的月份名稱 (相當於 **%b**)|
|**%H**|24 小時制的小時 (00-23)|
|**%I**|12 小時制 （01 到 12 個） 的|
|**%j**|以十進位數字 (001 到 366) 的一年天數|
|**%m**|月份，以十進位數字 （01 到 12 個）|
|**%M**|分鐘，以十進位數字 (00-59)|
|**%n**|新行字元 ( **\n**)|
|**%p**|地區設定的 a.m./p.m. 12 小時制的指標|
|**%r**|地區設定的 12 小時制的時間|
|**%R**|相當於 **%h:%m%M**|
|**%S**|第二個，以十進位數字 (00-59)|
|**%t**|水平定位字元 ( **\t**)|
|**%T**|相當於 **%h:%m: %s**，ISO 8601 時間格式|
|**%u**|以十進位數字 (1-7; 的 ISO 8601 週間日星期一是 1）|
|**%U**|以十進位數字表示的年份的週數 (00-53)，其中第一個星期日是第 1 週的第一天|
|**%V**|ISO 8601 週數，以十進位數字 (00-53)|
|**%w**|以十進位數字的週間日 (0-6;星期日是 0）|
|**%W**|以十進位數字表示的年份的週數 (00-53)，其中的第一個星期一是第 1 週的第一天|
|**%x**|地區設定的日期表示法|
|**%X**|地區設定的時間表示法|
|**%y**|不含世紀，以十進位數字的年份 (00-99)|
|**%Y**|含世紀的年份，以十進位數字表示|
|**%z**|從 UTC 的位移，採用 ISO 8601 格式;如果時區不明的任何字元|
|**%Z**|地區設定的時區名稱或時區縮寫，視登錄設定; 而定如果時區不明的任何字元|
|**%%**|百分比符號|

依照**printf**函式 **#** 旗標前面可以加上任何格式的程式碼。 在此情況下，格式代碼的意義會變更如下。

|格式化程式碼|意義|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**, **%#%**|**#** 會忽略旗標。|
|**%#c**|長時間的日期和時間表示法，適用於地區設定。 例如: 「 年 3 月 14日 1995 日星期二，12:41:29"。|
|**%#x**|完整日期表示法，適用於地區設定。 例如: 「 年 3 月 14日 1995 日星期二 」。|
|**%#d**， **%#D**， **%#e**， **%#F**， **%#H**， **%#I**， **%#j**， **%#m**， **%#M**， **%#r**， **%#R**， **%#S**， **%#T**， **%#U**， **%#V**， **%#W**， **%#y**， **%#Y**|移除前置的零或空格 （如果有的話）。|

所產生的 ISO 8601 週和每週為基礎的年度 **%V**， **%g**，並 **%G**，其中的第 1 週是包含年 1 月 4 日，也就是第一週開始於星期一、 一週會使用包含至少四天的年份的週次。 如果第 2 個為一年的第一個星期一，第 3 個或第 4 個，上述的天屬於上述一年的最後一週。 這些天， **%V** 53，並會取代 **%g**並 **%G**會取代先前的年度的數字。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**並 **_wcsftime_l**是 Microsoft 特有的函式。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
