---
title: main 函式和命令列引數C++（）
description: Main 函式是C++程式的進入點。
ms.date: 12/10/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
ms.openlocfilehash: 95e774700c63dc815f6d814bfda84a38a38d4e6e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302395"
---
# <a name="main-function-and-command-line-arguments"></a>main 函式和命令列引數

所有C++程式都必須具有 `main` 函式。 如果您嘗試在沒有 main C++函式的情況下編譯 *.exe*專案，編譯器將會引發錯誤。 （動態連結程式庫和靜態程式庫沒有 `main` 函數）。`main` 函式是您的原始程式碼開始執行的位置，但在程式進入 `main` 函式之前，所有沒有明確初始化運算式的靜態類別成員都會設定為零。 在 Microsoft C++中，全域靜態物件也會在進入 `main`之前初始化。 有數項限制適用于不適用於任何其他C++函式的 `main` 函數。 `main` 函式：

- 無法多載（請參閱[函數](function-overloading.md)多載）。
- 不能宣告為**inline**。
- 不能宣告為**static**。
- 無法取得自己的位址。
- 不能被呼叫。

`main` 的宣告語法如下：

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 特定的**

如果您的原始程式檔使用 Unicode 寬字元，您可以使用 `wmain`，也就是 `main`的寬字元版本。 `wmain` 的宣告語法如下：

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

您也可以使用在 tchar 中定義的 `_tmain`。 除非定義 _UNICODE，否則 `_tmain` 會解析為 `main`。 在此情況下，`_tmain` 會解析成 `wmain`。

如果未指定任何傳回值，則編譯器會提供傳回值零。 或者，`main` 和 `wmain` 函數可以宣告為傳回**void** （沒有傳回值）。 如果您宣告 `main` 或 `wmain` 傳回**void**，則無法使用[return](../cpp/return-statement-in-program-termination-cpp.md)語句將結束代碼傳回至父進程或作業系統。 若要在 `main` 或 `wmain` 宣告為**void**時傳回結束代碼，您必須使用[exit](../cpp/exit-function.md)函式。

**END Microsoft 特定的**

## <a name="command-line-arguments"></a>命令列引數

`main` 或 `wmain` 的引數可讓您輕鬆地對引數進行命令列剖析，並可選擇是否要存取環境變數。 `argc` 和 `argv` 的類型是由語言定義。 `argc`、`argv`和 `envp` 的名稱是傳統的，但您可以將其命名為任何您喜歡的名稱。

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

引數定義如下：

*argc*<br/>
包含*argv*中後面的引數計數的整數。 *Argc*參數一律大於或等於1。

*argv*<br/>
以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例，`argv[0]` 是用來叫用程式的命令，`argv[1]` 是第一個命令列引數，依此類推，直到 `argv[argc]`，這一律為 Null。 如需隱藏命令列處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。

第一個命令列引數一定是 `argv[1]`，而最後一個是 `argv[argc - 1]`。

> [!NOTE]
> 依照慣例，`argv[0]` 是用來叫用程式的命令。 不過，您可以使用[CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)來產生進程，而且如果您同時使用第一個和第二個引數（*lpApplicationName*和*lpCommandLine*），`argv[0]` 可能不是可執行檔名稱;使用[GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)來取出可執行檔名稱及其完整路徑。

**Microsoft 特定的**

*envp*<br/>
在許多 UNIX 系統中， *envp*陣列是通用的延伸模組，可在 Microsoft C++中使用。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列由 NULL 項目終止。 它可以宣告為**char** （`char *envp[]`）指標的陣列，或宣告為**char** （`char **envp`）指標的指標。 如果您的程式使用 `wmain` 而不是 `main`，請使用**wchar_t**資料類型，而不是**char**。 傳遞至 `main` 的環境區塊，`wmain` 是目前環境的「凍結」複本。 如果您後續透過呼叫 `putenv` 或 `_wputenv`來變更環境，則目前環境（如 `getenv` 或 `_wgetenv` 和 `_environ` 或 `_wenviron` 變數所傳回）將會變更，但 envp 所指向的區塊不會變更。 如需隱藏環境處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**END Microsoft 特定的**

### <a name="example"></a>範例

下列範例顯示如何使用*argc*、 *argv*和*envp*引數來 `main`：

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

## <a name="parsing-c-command-line-arguments"></a>剖析C++命令列引數

**Microsoft 特定的**

當解讀作業系統C++命令列上指定的引數時，Microsoft C/啟動程式碼會使用下列規則：

- 引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。

- 插入號字元 (^) 不會被辨識為逸出字元或分隔符號。 該字元會由作業系統中的命令列剖析器完整處理，然後才會傳遞至程式中的 `argv` 陣列。

- 雙引號（"*string*"）括住的字串會被視為單一引數，不論中包含的空白字元為何。 有引號的字串可以內嵌到引數中。

- 前面有反斜線 (\\") 的雙引號會解譯為常值雙引號字元 (")。

- 反斜線會逐字解譯，除非後面緊接著雙引號。

- 如果雙引號後面加上偶數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，並將雙引號轉譯為字串分隔符號。

- 如果雙引號後面加上奇數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，而雙引號會被其餘的反斜線「轉義」，使常值雙引號（"）放在 `argv`中。

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

|命令列輸入|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**END Microsoft 特定的**

## <a name="wildcard-expansion"></a>萬用字元展開

**Microsoft 特定的**

您可以在命令列上使用問號 (?) 和星號 (*) 等萬用字元來指定檔案名稱和路徑引數。

命令列引數是由稱為 `_setargv` 的常式（或寬字元環境中的 `_wsetargv`）處理，預設不會將萬用字元展開為 `argv` 字串陣列中的個別字串。 如需啟用萬用字元展開的詳細資訊，請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。

**END Microsoft 特定的**

## <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理

**Microsoft 特定的**

如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 此常式會 `_setargv` 呼叫，並在[萬用字元展開](../cpp/wildcard-expansion.md)中說明。 若要隱藏其使用方式，請定義不在包含 `main` 函式的檔案中執行任何工作的常式，並將其命名為 `_setargv`。 接著，`_setargv`的定義會滿足 `_setargv` 的呼叫，而且不會載入程式庫版本。

同樣地，如果您從未透過 `envp` 引數來存取環境資料表，您可以提供自己的空白常式來取代 `_setenvp`（環境處理常式）。 就像 `_setargv` 函數一樣，`_setenvp` 必須宣告為**extern "C"** 。

您的程式可能會呼叫 C 執行時間程式庫中的 `spawn` 或 `exec` 系列的常式。 如果是這種情況，您就不應該隱藏環境處理常式，因為這個常式會用來將環境從父處理序傳遞至子處理序。

**END Microsoft 特定的**

## <a name="see-also"></a>請參閱

[基本概念](../cpp/basic-concepts-cpp.md)