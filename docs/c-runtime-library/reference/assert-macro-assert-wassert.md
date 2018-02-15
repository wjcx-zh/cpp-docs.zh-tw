---
title: "assert 巨集、_assert、_wassert | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757571b9de1dbf86040ecd83ae86c4038207798e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="assert-macro-assert-wassert"></a>assert 巨集、_assert、_wassert
評估運算式；當結果為 `false`時，列印診斷資訊並中止程式。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `expression`  
 評估為非零 (`true`) 或 0 (`false`) 的純量運算式 (包括指標運算式)。  
  
 `message`  
 要顯示的訊息。  
  
 `filename`  
 判斷提示失敗之原始程式檔的名稱。  
  
 `line`  
 判斷提示失敗之原始程式檔中的行號。  
  
## <a name="remarks"></a>備註  
 `assert` 巨集通常可用來找出程式開發期間的邏輯錯誤。 此巨集可在發生未預期的情況時，用來停止程式執行，方法是實作 `expression` 引數，僅在程式運作異常時評估為 `false` 。 您可以定義巨集 `NDEBUG`，在編譯時期關閉判斷提示檢查。 您可以使用 `assert` 命令列選項關閉 **assert** 巨集，而不需要修改原始程式檔。 您可以在包含 \<assert.h> 前使用 `#define NDEBUG` 指示詞，以關閉來源程式碼的 `assert` 巨集。  
  
 當 `expression` 評估為 `false` (0)，並呼叫 [abort](../../c-runtime-library/reference/abort.md) 以終止程式執行時，`assert` 巨集會列印診斷訊息。 如果 `expression` 為 `true` (非零)，則不會採取任何動作。 診斷訊息包含失敗的運算式，以及判斷提示失敗之原始程式檔的名稱及其中的行號。  
  
 診斷訊息會以寬字元列印。 因此，即使運算式中有 Unicode 字元，也會如預期般運作。  
  
 診斷訊息的目的地取決於呼叫常式的應用程式類型。 主控台應用程式一律會透過 `stderr`接收訊息。 在 Windows 應用程式中， `assert` 會呼叫 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) 函式建立訊息方塊，連同 [確定]  按鈕一起顯示訊息。 當使用者按一下 [確定] 時，程式會立即中止。  
  
 當應用程式連結到執行階段程式庫的偵錯版本時， `assert` 會建立含有三個按鈕的訊息方塊：[中止] 、[重試] 和 [忽略] 。 如果使用者按一下 [中止] ，程式會立即中止。 如果使用者按一下 [重試] ，會呼叫偵錯工具，而使用者可以偵錯程式是否已啟用 Just-In-Time (JIT) 偵錯。 如果使用者按一下 [忽略] ， `assert` 會繼續正常執行：建立含有 [確定]  按鈕的訊息方塊。 請注意，如果在發生錯誤情況時按一下 [忽略]  ，可能會導致未定義的行為。  
  
 如需 CRT 偵錯的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。  
  
 `_assert` 和 `_wassert` 函式是內部 CRT 函式。 這些函式可協助減少物件檔案中用以支援判斷提示所需的程式碼。 不建議您直接呼叫這些函式。  
  
 未定義 `assert` 時，C 執行階段程式庫的發行和偵錯版本中會啟用 `NDEBUG` 巨集。 定義 `NDEBUG` 時，此巨集雖然可以使用，但不會評估其引數且沒有作用。 啟用時， `assert` 巨集會為其實作呼叫 `_wassert` 。 也可以使用其他判斷提示巨集 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)、[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，但只有在 [_DEBUG](../../c-runtime-library/debug.md) 巨集已定義並位於連結到 C 執行階段程式庫之偵錯版本的程式碼時，這些巨集才會評估傳遞給它們的運算式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`assert`, `_wassert`|\<assert.h>|  
  
 在標頭檔中無法使用 `_assert` 函式的簽章。 未定義 `_wassert` 巨集時，只能使用 `NDEBUG` 函式的簽章。  
  
## <a name="example"></a>範例  
 在這個程式中， `analyze_string` 函式使用 `assert` 巨集來測試幾個與字串和長度相關的條件。 如果任何一個條件失敗，程式會列印訊息，指出失敗的原因。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [_DEBUG](../../c-runtime-library/debug.md)