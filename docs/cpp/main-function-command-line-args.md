---
title: 'main 函數和命令列引數 (c + +) '
description: main函數是 c + + 程式的進入點。
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: b27668c3c7ce77e4369af144bb8be4efb695e522
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499815"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>main 函數和命令列引數

所有 c + + 程式都必須有 `main` 函數。 如果您嘗試在沒有函式的情況下編譯 c + + *.exe* 專案 main ，編譯器將會引發錯誤。  (動態連結程式庫和程式庫沒有 static 函式 `main` 。 ) 函式 `main` 是您的原始程式碼開始執行的位置，但是在程式進入函式之前 `main` ，所有 static 沒有明確初始化運算式的類別成員都會設定為零。 在 Microsoft c + + 中，全域 static 物件也會在進入之前初始化 `main` 。 有幾項限制適用于 `main` 不會套用至任何其他 c + + 函式的函式。 `main`函數：

- 無法多載 (請參閱 [函數](function-overloading.md) 多載) 。
- 無法宣告為 **`inline`** 。
- 無法宣告為 **`static`** 。
- 無法取得自己的位址。
- 不能被呼叫。

main函數沒有宣告，因為它已內建在語言中。 如果有的話，的宣告語法如下所 `main` 示：

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 特定的**

如果您的原始程式檔使用 Unicode 寬 char acters，您可以使用 `wmain` ，也就是的寬 char acter 版本 `main` 。 `wmain` 的宣告語法如下：

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

您也可以使用 `_tmain` 在 t. h 中定義的 char 。 `_tmain` 除非已 `main` 定義 _UNICODE，否則解析為。 在此情況下，`_tmain` 會解析成 `wmain`。

如果未指定任何傳回值，則編譯器會提供傳回值零。 或者，和函式 `main` `wmain` 可以宣告為傳回 **`void`** (沒有) 的傳回值。 如果您宣告 `main` 或傳回 `wmain` **`void`** ，就無法 exit 使用 [return](./program-termination.md) 語句，將程式碼傳回父進程或作業系統。 若要 exit 在宣告或宣告為時傳回程序代碼 `main` `wmain` **`void`** ，您必須使用 [exit](./program-termination.md) 函數。

**結束 Microsoft 專有**

## <a name="command-line-arguments"></a>命令列引數

或的引數可 `main` `wmain` 讓您方便地命令列剖析引數，並選擇性地存取環境變數。 `argc` 和 `argv` 的類型是由語言定義。 名稱 `argc` 、 `argv` 和 `envp` 都是傳統的，但您可以將它們命名為任何您喜歡的名稱。

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

引數定義如下：

*argc*<br/>
整數，其中包含後續的引數計數 *argv* 。 *argc* 參數一律大於或等於1。

*argv*<br/>
以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例， `argv[0]` 是用來叫用程式的命令， `argv[1]` 是第一個命令列引數，依此類推，直到 `argv[argc]` ，一律為 Null。 如需隱藏命令列處理的詳細資訊，請參閱 [自訂命令列處理]() 。

第一個命令列引數一定是 `argv[1]`，而最後一個是 `argv[argc - 1]`。

> [!NOTE]
> 依照慣例， `argv[0]` 這是用來叫用程式的命令。 但是， [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 如果您同時使用第一個和第二個引數 (*LpApplicationName* 和 *lpCommandLine*) ， `argv[0]` 可能不是可執行檔名稱，也可能不是可執行 [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 檔案名稱，而是使用取得可執行檔名稱及其完整路徑。

**Microsoft 特定的**

*envp*<br/>
*envp* 陣列是許多 UNIX 系統中常見的擴充功能，用於 Microsoft c + +。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列由 NULL 項目終止。 您可以將它宣告為指標的陣列，以 **`char`** (`char *envp[]`) 或指標指向 **`char`** () 的指標 `char **envp` 。 如果您的程式使用 `wmain` 而非 `main` ，請使用 **`wchar_t`** 資料類型，而不是 **`char`** 。 傳遞至的環境區塊 `main` `wmain` 是目前環境的「凍結」複本。 如果您之後透過對或的呼叫來變更 `putenv` 環境 `_wputenv` ，則目前的環境 (由或所傳回， `getenv` `_wgetenv` 而 `_environ` 或  `_wenviron` 變數) 將會變更，但指向的區塊 envp 不會變更。 如需隱藏環境處理的詳細資訊，請參閱 [自訂命令列處理]() 。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專有**

### <a name="example"></a>範例

下列範例顯示如何使用 *argc* 、 *argv* 和 *envp* 引數來 `main` ：

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>剖析 c + + 命令列引數

**Microsoft 特定的**

解釋作業系統命令列上指定的引數時，Microsoft C/c + + 啟始程式碼會使用下列規則：

- 引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。

- 插入號 char acter (^) 不會被辨識為 escape char acter 或分隔符號。 charActer 由作業系統中的命令列剖析器完全處理，然後才會傳遞至 `argv` 程式中的陣列。

- 以雙引號括住的字串 ( "*string*" ) 會被視為單一引數，不論包含的空白字元為何。 有引號的字串可以內嵌到引數中。

- 前面加上反斜線 (\\ ") 的雙引號會被視為常值雙引號 char acter (" ) 。

- 反斜線會逐字解譯，除非後面緊接著雙引號。

- 如果有偶數的反斜線後面加上雙引號，則會在 `argv` 陣列中為每一對反斜線加上一個反斜線，並將雙引號視為字串分隔符號。

- 如果反斜線後面加上奇數數目的反斜線，則會在每對反斜線的陣列中放入一個反斜線， `argv` 而雙引號會以反斜線來「轉義」 main ，而導致常值雙引號 ( ") 放入 `argv` 。

### <a name="example"></a>範例

下列程式示範如何傳遞命令列引數：

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

下表顯示範例輸入和預期的輸出，示範上述清單中的規則。

### <a name="results-of-parsing-command-lines"></a>剖析命令列的結果

|命令列輸入|argv[1]|argv[2]|argv3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**結束 Microsoft 專有**

## <a name="wildcard-expansion"></a>萬用字元展開

**Microsoft 特定的**

您可以在命令列上使用問號 (?) 和星號 (*) 等萬用字元來指定檔案名稱和路徑引數。

命令列引數是由稱為 (的常式 `_setargv` 或 `_wsetargv` char acter 環境中的) （預設不會將萬用字元擴充至字串陣列中的個別字串）來處理 `argv` 。 如需啟用萬用字元擴充的詳細資訊，請參閱 [擴充萬用字元引數](../c-language/expanding-wildcard-arguments.md)。

**結束 Microsoft 專有**

## <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理

**Microsoft 特定的**

如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 這個常式會被呼叫 `_setargv` ，並且會在 [萬用字元展開]()中說明。 若要隱藏其使用方式，請定義不在包含函式的檔案中執行任何動作的常式， `main` 並為其命名 `_setargv` 。 的呼叫 `_setargv` 接著會滿足您的定義 `_setargv` ，而且不會載入程式庫版本。

同樣地，如果您從未透過引數存取環境資料表 `envp` ，您可以提供自己的空白常式來取代 `_setenvp` 環境處理常式。 就像函式一樣 `_setargv` ， `_setenvp` 必須宣告為** extern "C"**。

您的程式可能會呼叫 `spawn` `exec` C 執行時間程式庫中的或系列常式。 如果有的話，您不應該隱藏環境處理常式，因為此常式是用來將環境從父進程傳遞至子進程。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)
