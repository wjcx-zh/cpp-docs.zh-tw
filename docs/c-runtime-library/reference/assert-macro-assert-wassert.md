---
title: assert 巨集、_assert、_wassert
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: badca46a0793e51602f0de87dfca21816dcd6295
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939613"
---
# <a name="assert-macro-_assert-_wassert"></a>assert 巨集、_assert、_wassert

評估運算式，並在結果為**false**時，列印診斷訊息並中止程式。

## <a name="syntax"></a>語法

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>參數

*expression*<br/>
評估為非零（**true**）或0（**false**）的純量運算式（包括指標運算式）。

*message*<br/>
要顯示的訊息。

*filename*<br/>
判斷提示失敗之原始程式檔的名稱。

*line*<br/>
判斷提示失敗之原始程式檔中的行號。

## <a name="remarks"></a>備註

**Assert**宏通常用來識別程式開發期間的邏輯錯誤。 當未預期的情況發生時，請使用它來停止程式執行，方法是在程式運作不正確時，將*運算式*引數實作為評估為**false** 。 您可以藉由定義宏**NDEBUG**，在編譯時期關閉判斷提示檢查。 您可以使用**assert**命令列選項來關閉**assert**宏，而不需要修改原始程式檔。 您可以藉由\<在 assert 中使用`#define NDEBUG`指示詞，在原始程式碼中關閉 assert 宏。 h > 包含在內。

當*expression*評估為**false** （0）時， **assert**宏會列印診斷訊息，並呼叫[abort](abort.md)來終止程式執行。 如果*expression*為**true** （非零），則不會採取任何動作。 診斷訊息包含失敗的運算式，以及判斷提示失敗之原始程式檔的名稱及其中的行號。

診斷訊息會以寬字元列印。 因此，即使運算式中有 Unicode 字元，也會如預期般運作。

診斷訊息的目的地取決於呼叫常式的應用程式類型。 主控台應用程式一律會透過**stderr**接收訊息。 在以 Windows 為基礎的應用程式中， **assert**會呼叫 Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)函式來建立訊息方塊，以顯示訊息和 **[確定]** 按鈕。 當使用者按一下 [確定]時，程式會立即中止。

當應用程式與執行時間程式庫的 debug 版本連結時， **assert**會建立含有三個按鈕的訊息方塊：[**中止**]、[**重試**] 和 [**忽略**]。 如果使用者按一下 [中止]，程式會立即中止。 如果使用者按一下 [重試]，會呼叫偵錯工具，而使用者可以偵錯程式是否已啟用 Just-In-Time (JIT) 偵錯。 如果使用者按一下 [**忽略**] **，則**判斷提示會繼續正常執行：建立含有 [**確定]** 按鈕的訊息方塊。 請注意，如果在發生錯誤情況時按一下 [忽略] ，可能會導致未定義的行為。

如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

**_Assert**和 **_wassert**函式是內部 CRT 函式。 這些函式可協助減少物件檔案中用以支援判斷提示所需的程式碼。 不建議您直接呼叫這些函式。

未定義**NDEBUG**時，會在 C 執行時間程式庫的發行和 debug 版本中啟用**assert**宏。 當定義**NDEBUG**時，可以使用宏，但不會評估其引數且不會有任何作用。 當它啟用時， **assert**宏會呼叫 **_wassert**以進行其實作為。 其他判斷提示巨集 [_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)也可以使用，但只有在 [_DEBUG](../../c-runtime-library/debug.md) 巨集已定義並位於連結到 C 執行階段程式庫之偵錯版本的程式碼時，這些巨集才會評估傳遞給它們的運算式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**assert**、 **_wassert**|\<assert.h>|

標頭檔中無法使用 **_assert**函式的簽章。 只有在未定義**NDEBUG**宏時，才可以使用 **_wassert**函數的簽章。

## <a name="example"></a>範例

在此程式中， **analyze_string**函數會使用**assert**宏來測試數個與字串和長度相關的條件。 如果任何一個條件失敗，程式會列印訊息，指出失敗的原因。

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

程式會產生以下輸出：

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

判斷提示失敗之後，根據作業系統和執行階段程式庫的版本，您可能會看到含有下列訊息的訊息方塊：

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

如果已安裝偵錯工具，請選擇 [偵錯] 按鈕以啟動偵錯工具，或選擇 [關閉程式] 結束。

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
