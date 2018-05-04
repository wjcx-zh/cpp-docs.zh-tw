---
title: assert 巨集、_assert、_wassert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0318abde877e9b647c1781408d2e22cc9d70824e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="assert-macro-assert-wassert"></a>assert 巨集、_assert、_wassert

評估運算式，結果是**false**、 列印診斷訊息，並中止程式。

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

*運算式*純量運算式 （包括指標運算式） 評估為非零 (**true**) 或 0 (**false**)。

*訊息*来顯示的訊息。

*檔名*名稱的來源檔案中失敗的判斷提示。

*行*失敗的判斷提示的原始程式檔中的行號。

## <a name="remarks"></a>備註

**Assert**巨集通常用來在程式開發期間識別出邏輯錯誤。 用於藉由實作發生非預期的狀況時停止程式執行*運算式*引數評估為**false**僅當程式運作異常。 判斷提示檢查可以關閉在編譯時期藉由定義巨集**NDEBUG**。 您可以關閉**assert**巨集，而不修改原始程式檔使用 **/DNDEBUG**命令列選項。 您可以關閉**assert**巨集程式碼中使用`#define NDEBUG`指示詞之前\<assert.h > 就會包含。

**Assert**巨集會列印診斷訊息時*運算式*評估為**false** (0) 和呼叫[中止](abort.md)終止程式執行。 如果未採取任何動作*運算式*是**true** （非零）。 診斷訊息包含失敗的運算式，以及判斷提示失敗之原始程式檔的名稱及其中的行號。

診斷訊息會以寬字元列印。 因此，即使運算式中有 Unicode 字元，也會如預期般運作。

診斷訊息的目的地取決於呼叫常式的應用程式類型。 主控台應用程式一定會收到訊息通過**stderr**。 在 Windows 架構應用程式中， **assert**呼叫 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505)函式來建立訊息方塊以顯示訊息和**確定**按鈕。 當使用者按一下 [確定] 時，程式會立即中止。

當應用程式的執行階段程式庫的偵錯版本連結時**判斷提示**建立訊息方塊具有三個按鈕：**中止**，**重試**，和**忽略**。 如果使用者按一下 [中止] ，程式會立即中止。 如果使用者按一下 [重試] ，會呼叫偵錯工具，而使用者可以偵錯程式是否已啟用 Just-In-Time (JIT) 偵錯。 如果使用者按一下**忽略**，**判斷提示**會繼續正常執行： 建立的訊息方塊具有**確定** 按鈕。 請注意，如果在發生錯誤情況時按一下 [忽略]  ，可能會導致未定義的行為。

如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

**_Assert**和 **_wassert**函式是內部 CRT 函式。 這些函式可協助減少物件檔案中用以支援判斷提示所需的程式碼。 不建議您直接呼叫這些函式。

**Assert** C 執行階段程式庫的發行和偵錯版本中已啟用巨集時**NDEBUG**未定義。 當**NDEBUG**是定義，巨集，可用但不會評估其引數並沒有任何作用。 當它啟用時， **assert**巨集呼叫 **_wassert**為其實作。 也可以使用其他判斷提示巨集 [_ASSERT](assert-asserte-assert-expr-macros.md)、[_ASSERTE](assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)，但只有在 [_DEBUG](../../c-runtime-library/debug.md) 巨集已定義並位於連結到 C 執行階段程式庫之偵錯版本的程式碼時，這些巨集才會評估傳遞給它們的運算式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**判斷提示**， **_wassert**|\<assert.h>|

簽章 **_assert**函式是未標頭檔中。 簽章 **_wassert**函式時，才可以使用**NDEBUG**巨集未定義。

## <a name="example"></a>範例

此程式**analyze_string**函式使用**assert**巨集來測試幾個條件與字串和長度。 如果任何一個條件失敗，程式會列印訊息，指出失敗的原因。

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

如果已安裝偵錯工具，請選擇 [偵錯]  按鈕以啟動偵錯工具，或選擇 [關閉程式]  結束。

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
