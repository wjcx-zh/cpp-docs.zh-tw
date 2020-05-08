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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9d262371369681cbbd5975a733950d6c4150fd88
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920026"
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

*strDest*<br/>
輸出字串。

*maxsize*<br/>
*StrDest*緩衝區的大小，以字元（**char**或**wchar_t**）來測量。

*format*<br/>
格式控制字串。

*timeptr*<br/>
**tm**資料結構。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strftime**會傳重播在*strDest*中的字元數，而**wcsftime**會傳回對應的寬字元數。

如果字元總數（包括終止的 null）大於*maxsize*，則**strftime**和**wcsftime**都會傳回0，而*strDest*的內容則不確定。

*StrDest*中的字元數等於*格式*的常值字元數，以及可以透過格式化程式碼加入*格式*的任何字元。 字串的結束 Null 不會計入傳回值。

## <a name="remarks"></a>備註

**Strftime**和**wcsftime**函式會根據提供的*格式*引數來格式化*timeptr*中的**tm**時間值，並將結果儲存在緩衝區*strDest*中。 最多可將*maxsize*字元放在字串中。 如需*timeptr*結構中欄位的描述，請參閱[asctime](asctime-wasctime.md)。 **wcsftime**是**strftime**的寬字元對應項;其字串指標引數會指向寬字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果*strDest*、 *format*或*timeptr*為 null 指標，或如果*timeptr*定址的**tm**資料結構無效（例如，如果它包含超出時間或日期的範圍值），或如果*格式*字串包含不正確格式代碼，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回0，並將**errno**設為**EINVAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*Format*引數是由一或多個代碼所組成;如同在**printf**中，格式化程式碼的前面會加上百分比**%** 符號（）。 不**%** 是以開頭的字元會原封不動地複製到*strDest*。 目前地區設定的 [ **LC_TIME** ] 分類會影響**strftime**的輸出格式。 （如需**LC_TIME**的詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)）。**Strftime**和**wcsftime**函數會使用目前設定的地區設定。 這些函式的 **_strftime_l**和 **_wcsftime_l**版本都相同，不同之處在于它們會採用地區設定作為參數，並使用它，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函數支援下列格式設定代碼：

|||
|-|-|
|程式碼|取代字串|
|**% a**|地區設定中縮寫的工作日名稱|
|**% A**|地區設定中的完整工作日名稱|
|**% b**|地區設定中的縮寫月份名稱|
|**% B**|地區設定中的完整月份名稱|
|**% c**|適用於地區設定的日期和時間表示|
|**% C**|年份除以100並截斷為整數（以十進位數表示）（00−99）|
|**% d**|以十進位數表示的月份日（01-31）|
|**% D**|相當於 **% m/% d/% y**|
|**% e**|以十進位數（1-31）為單位的月份日，其中的單一數位前面會加上空格|
|**% F**|相當於 **% Y-% m-% d**|
|**% g**|ISO 8601 以周為基礎之年份的最後2個數字，表示為十進位數（00-99）|
|**% G**|ISO 8601 以周為基礎的年份，以十進位數表示|
|**% h**|縮寫的月份名稱（相當於 **% b**）|
|**% H**|24小時制的小時（00-23）|
|**% I**|12小時制的小時（01-12）|
|**% j**|一年中的日期，表示為十進位數（001-366）|
|**% m**|Month 作為十進位數（01-12）|
|**% M**|以十進位數表示的分鐘（00-59）|
|**% n**|換行字元（**\n**）|
|**% p**|地區設定的 A.M./P.M。 12 小時制的指標|
|**% r**|地區設定的12小時制時間|
|**% R**|相當於 **% H:%M**|
|**% S**|秒做為十進位數（00-59）|
|**% t**|水準定位字元（**\t**）|
|**% T**|相當於 **% H:%M：% S**，ISO 8601 時間格式|
|**% u**|ISO 8601 工作日，以十進位數表示（1-7;星期一為1）|
|**% U**|做為十進位數的年份周數（00-53），其中第一個星期日是第1周的第一天|
|**% V**|ISO 8601 周數位，以十進位數表示（00-53）|
|**% w**|以十進位數表示的工作日（0-6;星期日是0）|
|**% W**|做為十進位數的年份周數（00-53），其中第一個星期一是第一周的第一天|
|**% x**|地區設定的日期標記法|
|**% X**|地區設定的時程表示法|
|**% y**|不含世紀的年份，以十進位數表示（00-99）|
|**% Y**|含世紀的年份，以十進位數字表示|
|**% z**|UTC 的時差，格式為 ISO 8601，如果時區不明，則不會有任何字元|
|**% Z**|地區設定的時區名稱或時區縮寫，視登錄設定而定;如果時區不明，則不會有任何字元|
|**%%**|百分比符號|

如同在**printf**函式中， **#** 旗標可能會在任何格式化程式碼之前加上前置詞。 在此情況下，格式代碼的意義會變更如下。

|格式化程式碼|意義|
|-----------------|-------------|
|**% #a**， **% #A**， **% #b**， **% #B**， **% #g**， **% #G**， **% #h**， **% #n**， **% #p**， **% #t**， **% #u**， **% #w**， **% #X**， **% #z**， **% #Z**，**%#%**|**#** 已忽略旗標。|
|**% #c**|完整日期和時程表示法，適用于地區設定。 例如：「1995 年 3 月 14 日星期二 12:41:29」。|
|**% #x**|完整日期標記法，適用于地區設定。 例如：「1995 年 3 月 14 日星期二」。|
|**% #d**， **% #D**， **% #e**， **% #F**， **% #H**， **% #I**， **% #j**， **% #m**， **% #M**， **% #r**， **% #R**， **% #S**， **% #T**， **%** **#U，% #V**， **% #W**， **%** **#y，% #Y**|移除前置的零或空格（如果有的話）。|

由 **% V**、 **% g**和 **% g**所產生的 ISO 8601 周和以周為基礎的年份，會使用從星期一開始的周，其中第1周是包含1月4日的一周，其中至少包含四天的年份。 如果今年的第一個星期一是第二、第三或第4個，則前幾天是上一年最後一周的一部分。 在那些日子中， **% V**會取代為53，而 **% g**和 **% g**都會取代為前一年的數位。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**和 **_wcsftime_l**函式為 Microsoft 特有的功能。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [time](time-time32-time64.md) 的範例。

## <a name="see-also"></a>另請參閱

[語言](../../c-runtime-library/locale.md) <br/>
[時間管理](../../c-runtime-library/time-management.md) <br/>
[字串操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
