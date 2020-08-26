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
ms.openlocfilehash: 36a84c5de41f3358adbcba42010ed8e6f3c83939
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846572"
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
*StrDest*緩衝區的大小，以字元 (**`char`** 或) 來測量 **`wchar_t`** 。

*format*<br/>
格式控制字串。

*timeptr*<br/>
**tm** 資料結構。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strftime** 會傳重播置在 *strDest* 中的字元數，而 **wcsftime** 則會傳回對應的寬字元數。

如果字元總數（包括結束的 null）超過 *maxsize*， **strftime** 和 **wcsftime** 都會傳回0，而 *strDest* 的內容則為不定。

*StrDest*中的字元數等於*格式*的常值字元數，以及可能透過格式化程式碼新增至*格式*的任何字元。 字串的結束 Null 不會計入傳回值。

## <a name="remarks"></a>備註

**Strftime**和**wcsftime**函式會根據所提供的*格式*引數來格式化*timeptr*中的**tm**時間值，並將結果儲存在緩衝區*strDest*中。 最多可將 *maxsize* 字元放在字串中。 如需 *timeptr* 結構中欄位的描述，請參閱 [asctime](asctime-wasctime.md)。 **wcsftime** 是 **strftime**的寬字元相等;其字串指標引數會指向寬字元字串。 除此之外，這些函式的行為相同。

這個函式會驗證它的參數。 如果*strDest*、 *format*或*timeptr*是 null 指標，或由*timeptr*定址的**tm**資料結構無效 (例如，如果它包含的時間或日期) 超出範圍值，或如果*格式*字串包含不正確格式化程式碼，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函數會傳回0，並將 **errno** 設定為 **EINVAL**。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*引數包含一個或多個程式碼;如同**printf**，格式化程式碼前面會加上百分比符號 (**%**) 。 開頭不是的字元 **%** 會原封不動地複製到 *strDest*。 目前地區設定的 **LC_TIME** 類別會影響 **strftime**的輸出格式。  (如需 **LC_TIME**的詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 ) **strftime** 和 **wcsftime** 函式會使用目前設定的地區設定。 這些函式的 **_strftime_l** 和 **_wcsftime_l** 版本完全相同，不同之處在于它們會採用地區設定作為參數，並使用該地區設定，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函式支援下列格式設定代碼：

|程式碼|取代字串|
|-|-|
|**% a**|地區設定中縮寫的工作日名稱|
|**% A**|地區設定中的完整工作日名稱|
|**% b**|地區設定中的縮寫月份名稱|
|**% B**|地區設定中的完整月份名稱|
|**% c**|適用於地區設定的日期和時間表示|
|**% C**|年份除以100，並截斷為整數，以十進位數 (00 − 99) |
|**% d**|以十進位數表示的月份日 (01-31) |
|**% D**|相當於 **% m/% d/% y**|
|**% e**|以十進位數表示的月份日 (1-31) ，其中的單一位數前面加上空格|
|**% F**|相當於 **% Y-% m-% d**|
|**% g**|以 ISO 8601 周為基礎之年份的最後2個數字 (00-99) |
|**% G**|ISO 8601 以周為基礎的年份，以十進位數表示|
|**% h**|縮寫的月份名稱 (等於 **% b**) |
|**% H**|以24小時制格式的小時 (00-23) |
|**% I**|12小時制的小時 (01-12) |
|**% j**|以十進位數表示的年份日 (001-366) |
|**% m**|以十進位數表示的月份 (01-12) |
|**% M**|以十進位數表示的分鐘 (00-59) |
|**% n**|分行符號 (**\n**) |
|**% p**|地區設定的 A.M./P.M。 12 小時制的指標|
|**% r**|地區設定的12小時制時鐘時間|
|**% R**|相當於 **% H:%M**|
|**% S**|第二個是十進位數 (00-59) |
|**% t**|水準定位字元 (**\t**) |
|**% T**|相當於 **% H:%M：% S**，ISO 8601 時間格式|
|**% u**|ISO 8601 weekday 的十進位數 (1-7;星期一為 1) |
|**% U**|年份的周數，以十進位數 (00-53) ，其中第一個星期日是第1周的第一天|
|**% V**|ISO 8601 周數，以十進位數 (00-53) |
|**% w**|以十進位數表示的工作日 (0-6;星期日為 0) |
|**% W**|年份的周數，以十進位數 (00-53) ，其中的第一個星期一是第1周的第一天|
|**% x**|地區設定的日期標記法|
|**% X**|地區設定的時程表示法|
|**% y**|沒有世紀的年份，以十進位數 (00-99) |
|**% Y**|含世紀的年份，以十進位數字表示|
|**% z**|UTC 的位移（以 ISO 8601 格式）;如果時區不明，則無字元|
|**% Z**|地區設定的時區名稱或時區縮寫，視登錄設定而定;如果時區不明，則無字元|
|**%%**|百分比符號|

如同在 **printf** 函式中， **#** 旗標可能會在任何格式化程式碼前面加上前置詞。 在此情況下，格式代碼的意義會變更如下。

|格式化程式碼|意義|
|-----------------|-------------|
|**% #a**， **% #A**， **% #b**， **% #B**， **% #g**， **% #G**， **% #h**， **% #n**， **% #p**， **% #t**， **% #u**， **% #w**， **% #X**， **% #z**， **% #Z**， **%#%**|**#** 已忽略旗標。|
|**% #c**|適用于地區設定的完整日期和時程表示法。 例如：「1995 年 3 月 14 日星期二 12:41:29」。|
|**% #x**|適用于地區設定的完整日期表示。 例如：「1995 年 3 月 14 日星期二」。|
|**% #d**， **% #D**， **% #e**， **% #F**， **% #H**， **% #I**， **% #j**， **% #m**， **% #M**， **% #r**， **% #R**， **% #S**， **% #T**， **% #U**，% **#V**， **% #W**，% **#y**， **% #Y**|移除前置零或空格 (如果有任何) 。|

由 **% V**、 **% g**和 **% g**所產生的 ISO 8601 星期和以周為基礎的年份，會使用從星期一開始的周，其中第1周是包含1月4日，第一周至少包含四天。 如果當年的第一個星期一是第二、第三個或第四個，則前一天是前一年的最後一周的一部分。 在這幾天， **% V** 會取代為53，而 **% g** 和 **% g** 會以前一年的數位取代。

> [!NOTE]
> 使用其中一個 `strftime` 具有 `tm` 從傳回之指標的函式時，透過 `gmtime` 和規範列印的值 `%Z` `%z` 將不會正確。 這是因為 `tm` C 標準所指定的結構不包含時區名稱或位移的資訊。 相反地，時區資訊是透過全域變數[ `_timezone` 和 `_dstbias` ](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)來填入。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**和 **_wcsftime_l**函式都是 Microsoft 特定的。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
