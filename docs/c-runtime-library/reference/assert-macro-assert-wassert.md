---
title: assert 巨集、_assert、_wassert
description: C 執行時間中 assert 宏和函式的效果。
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
ms.openlocfilehash: 071424f2201ceda43438fe1056801811fe444a01
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609084"
---
# <a name="assert-macro-_assert-_wassert"></a>assert 巨集、_assert、_wassert

評估運算式，並在結果為時 **`false`** 列印診斷訊息，並中止程式。

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
純量運算式 (包含) 的指標運算式，這些運算式會評估為非零 (**`true`**) 或 0 (**`false`**) 。

*message*<br/>
要顯示的訊息。

*filename*<br/>
判斷提示失敗之原始程式檔的名稱。

*line*<br/>
判斷提示失敗之原始程式檔中的行號。

## <a name="remarks"></a>備註

`assert` 巨集通常可用來找出程式開發期間的邏輯錯誤。 如果未預期的情況發生，請使用它來停止程式執行，方法是執行 *運算式* 引數，使其 **`false`** 只在程式正常運作時才評估為。 您可以藉由定義宏 **NDEBUG**，在編譯時期關閉判斷提示檢查。 您可以使用 `assert` 命令列選項關閉 **assert** 巨集，而不需要修改原始程式檔。 您可以在 `assert` 包含之前使用指示詞，在原始程式碼中關閉宏 `#define NDEBUG` \<assert.h> 。

`assert`當*運算式*評估為 **`false`** (0) 和呼叫 [`abort`](abort.md) 來停止程式執行時，宏會列印診斷訊息。 如果 *expression* **`true`** (非零) ，就不會採取任何動作。 診斷訊息包含失敗的運算式，以及判斷提示失敗之原始程式檔的名稱及其中的行號。

診斷訊息會以寬 (`wchar_t`) 字元列印。 因此，即使運算式中有 Unicode 字元，它仍會如預期般運作。

診斷訊息的目的地取決於呼叫常式的應用程式類型。 主控台應用程式會透過 **stderr**接收訊息。 在以 Windows 為基礎的應用程式中， `assert` 呼叫 Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) 函式來建立訊息方塊，以顯示具有三個按鈕的訊息： [ **中止**]、[ **重試**] 和 [ **忽略**]。 如果使用者按一下 [中止] ****，程式會立即中止。 如果使用者按一下 [重試] ****，會呼叫偵錯工具，而使用者可以偵錯程式是否已啟用 Just-In-Time (JIT) 偵錯。 如果使用者按一下 [ **略**過]，程式就會繼續正常執行。 當錯誤狀況存在時，按一下 [ **忽略** ] 可能會導致未定義的行為，因為不符合呼叫程式碼的前置條件。

若要覆寫預設輸出行為（不論應用程式類型為何），請呼叫 [`_set_error_mode`](set-error-mode.md) 以在輸出到 stderr 和顯示對話方塊行為之間進行選取。

在 `assert` 顯示其訊息之後，它會呼叫 [`abort`](abort.md) ，這會顯示具有 [  **中止**]、[ **重試**] 和 [ **略** 過] 按鈕的對話方塊。 [`abort`](abort.md) 結束程式，讓 [ **重試** ] 和 [ **略** 過] 按鈕不會在呼叫後繼續執行程式 `assert` 。 如果 `assert` 顯示對話方塊，則不會 [`abort`](abort.md) 顯示對話方塊。 唯一 [`abort`](abort.md) 顯示對話方塊的時機是將 `assert` 其輸出傳送到 stderr。

由於上述行為的結果，在偵測模式下呼叫時，一律會顯示對話方塊 `assert` 。 每個按鈕的行為都會在下表中捕捉。

|錯誤模式|輸出至 stderr (主控台/_OUT_TO_STDERR) |顯示對話方塊 (Windows/_OUT_TO_MSGBOX) |
|----------|----------------|------------------|
|中止|立即結束，結束代碼3|立即結束，結束代碼3|
|重試|在期間中斷偵錯工具 `abort`|在期間中斷偵錯工具 `assert`|
|忽略|完成結束時間 `abort`|繼續程式，如同判斷提示未引發 (可能會導致未定義的行為，因為不符合呼叫程式碼的前置條件) |

如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

`_assert` 和 `_wassert` 函式是內部 CRT 函式。 這些函式可協助減少物件檔案中用以支援判斷提示所需的程式碼。 我們不建議您直接呼叫這些函式。

`assert`未定義**NDEBUG**時，會在 C 執行時間程式庫的發行和偵測版本中啟用宏。 當定義了 **NDEBUG** 時，就可以使用宏，但不會評估其引數，也不會有任何作用。 當它啟用時，宏就會 `assert` 呼叫 `_wassert` 其實作為。 也可以使用其他判斷提示巨集 [_ASSERT](assert-asserte-assert-expr-macros.md)、[_ASSERTE](assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)，但只有在 [_DEBUG](../../c-runtime-library/debug.md) 巨集已定義並位於連結到 C 執行階段程式庫之偵錯版本的程式碼時，這些巨集才會評估傳遞給它們的運算式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`assert`, `_wassert`|\<assert.h>|

`_assert`標頭檔中無法使用函式的簽章。 `_wassert`只有在未定義**NDEBUG**宏時，才能使用函式的簽章。

## <a name="example"></a>範例

在這個程式中， **analyze_string** 函數會使用 `assert` 宏來測試與字串和長度相關的數個條件。 如果任何一個條件失敗，程式會列印訊息，指出失敗的原因。

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

判斷提示失敗之後，視作業系統和執行時間程式庫的版本而定，您可能會看到一個訊息方塊，其中包含類似下列內容：

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

如果已安裝偵錯工具，請選擇 [偵錯] **** 按鈕以啟動偵錯工具，或選擇 [關閉程式] **** 結束。

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[流程式控制制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[提高](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE _ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
