---
title: :::no-loc(main):::函數和命令列引數（c + +）
description: :::no-loc(main):::函數是 c + + 程式的進入點。
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(wmain):::'
- ':::no-loc(inline):::'
- ':::no-loc(static):::'
- ':::no-loc(_tmain):::'
- ':::no-loc(void):::'
- ':::no-loc(exit):::'
- ':::no-loc(argc):::'
- ':::no-loc(argv):::'
- ':::no-loc(envp):::'
- ':::no-loc(CreateProcess):::'
- ':::no-loc(GetModuleFileName):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(extern):::'
ms.openlocfilehash: 9fe7c7a0808584a70bffa541903866b3de364e5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213316"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>:::no-loc(main):::函數和命令列引數

所有 c + + 程式都必須有 `:::no-loc(main):::` 函數。 如果您嘗試在不使用函式的情況下編譯 c + + *.exe*專案 :::no-loc(main)::: ，編譯器將會引發錯誤。 （動態連結程式庫和程式庫 :::no-loc(static)::: 沒有 `:::no-loc(main):::` 函數）。`:::no-loc(main):::`函式是您的原始程式碼開始執行的位置，但是在程式進入 `:::no-loc(main):::` 函數之前，所有 :::no-loc(static)::: 沒有明確初始化運算式的類別成員都會設定為零。 在 Microsoft c + + 中，全域 :::no-loc(static)::: 物件也會在進入之前初始化 `:::no-loc(main):::` 。 有數項限制適用于 `:::no-loc(main):::` 不適用於任何其他 c + + 函式的函式。 函式 `:::no-loc(main):::` ：

- 無法多載（請參閱[函數](function-overloading.md)多載）。
- 不可以宣告為 **`:::no-loc(inline):::`** 。
- 不可以宣告為 **`:::no-loc(static):::`** 。
- 無法取得自己的位址。
- 不能被呼叫。

函式 :::no-loc(main)::: 不具有宣告，因為它是內建在語言中。 如果已經這麼做，的宣告語法 `:::no-loc(main):::` 看起來會像這樣：

```cpp
int :::no-loc(main):::();
int :::no-loc(main):::(int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[]);
```

**Microsoft 特定的**

如果您的原始程式檔使用 Unicode 寬 :::no-loc(char)::: acters，您可以使用 `:::no-loc(wmain):::` ，這是的寬 :::no-loc(char)::: acter 版本 `:::no-loc(main):::` 。 `:::no-loc(wmain):::` 的宣告語法如下：

```cpp
int :::no-loc(wmain):::( );
int :::no-loc(wmain):::(int :::no-loc(argc):::, :::no-loc(wchar_t)::: *:::no-loc(argv):::[], :::no-loc(wchar_t)::: *:::no-loc(envp):::[]);
```

您也可以使用 `:::no-loc(_tmain):::` 定義于 t-sql 中的 :::no-loc(char)::: 。 `:::no-loc(_tmain):::`除非已 `:::no-loc(main):::` 定義 _UNICODE，否則會解析為。 在此情況下，`:::no-loc(_tmain):::` 會解析成 `:::no-loc(wmain):::`。

如果未指定任何傳回值，則編譯器會提供傳回值零。 或者，和函式 `:::no-loc(main):::` `:::no-loc(wmain):::` 可以宣告為傳回 **`:::no-loc(void):::`** （沒有傳回值）。 如果您將 `:::no-loc(main):::` 或宣告 `:::no-loc(wmain):::` 為傳回 **`:::no-loc(void):::`** ，就無法 :::no-loc(exit)::: 使用[return](../cpp/return-statement-in-program-termination-cpp.md)語句將程式碼傳回給父進程或作業系統。 若要 :::no-loc(exit)::: 在將或宣告為時傳回程序代碼 `:::no-loc(main):::` `:::no-loc(wmain):::` **`:::no-loc(void):::`** ，您必須使用 [:::no-loc(exit):::](../cpp/:::no-loc(exit):::-function.md) 函數。

**結束 Microsoft 專有**

## <a name="command-line-arguments"></a>命令列引數

或的自 `:::no-loc(main):::` 變數 `:::no-loc(wmain):::` 允許引數的方便命令列剖析，並選擇性地存取環境變數。 `:::no-loc(argc):::` 和 `:::no-loc(argv):::` 的類型是由語言定義。 名稱 `:::no-loc(argc):::` 、 `:::no-loc(argv):::` 和 `:::no-loc(envp):::` 都是傳統的，但您可以將其命名為任何您喜歡的名稱。

```cpp
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char):::* :::no-loc(argv):::[], :::no-loc(char):::* :::no-loc(envp):::[]);
int :::no-loc(wmain):::( int :::no-loc(argc):::, :::no-loc(wchar_t):::* :::no-loc(argv):::[], :::no-loc(wchar_t):::* :::no-loc(envp):::[]);
```

引數定義如下：

*:::no-loc(argc):::*<br/>
包含後面的引數計數的整數 *:::no-loc(argv):::* 。 *:::no-loc(argc):::* 參數一律大於或等於1。

*:::no-loc(argv):::*<br/>
以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例， `:::no-loc(argv):::[0]` 是用來叫用程式的命令， `:::no-loc(argv):::[1]` 是第一個命令列引數，依此類推，直到 `:::no-loc(argv):::[:::no-loc(argc):::]` ，一律為 Null。 如需隱藏命令列處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。

第一個命令列引數一定是 `:::no-loc(argv):::[1]`，而最後一個是 `:::no-loc(argv):::[:::no-loc(argc)::: - 1]`。

> [!NOTE]
> 依照慣例， `:::no-loc(argv):::[0]` 是用來叫用程式的命令。 不過， [:::no-loc(CreateProcess):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 如果您同時使用第一個和第二個引數（*LpApplicationName*和*lpCommandLine*），則可以使用和來產生進程，而 `:::no-loc(argv):::[0]` 不可以是可執行檔名稱; 使用 [:::no-loc(GetModuleFileName):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 來抓取可執行檔名稱及其完整路徑。

**Microsoft 特定的**

*:::no-loc(envp):::*<br/>
*:::no-loc(envp):::* 陣列是許多 UNIX 系統中通用的延伸模組，用於 Microsoft c + +。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列由 NULL 項目終止。 它可以宣告為的指標陣列（），或是宣告為指標的 **`:::no-loc(char):::`** `:::no-loc(char)::: *:::no-loc(envp):::[]` 指標 **`:::no-loc(char):::`** （ `:::no-loc(char)::: **:::no-loc(envp):::` ）。 如果您的程式使用 `:::no-loc(wmain):::` ，而不是 `:::no-loc(main):::` ，請使用 **`:::no-loc(wchar_t):::`** 資料類型，而不是 **`:::no-loc(char):::`** 。 環境區塊會傳遞至 `:::no-loc(main):::` ，而且 `:::no-loc(wmain):::` 是目前環境的「凍結」複本。 如果您後續透過呼叫或變更環境 `putenv` `_wputenv` ，則目前環境（如 `getenv` 或 `_wgetenv` 和 `_environ` 或變數所傳回 `_wenviron` ）將會變更，但所指向的區塊 :::no-loc(envp)::: 不會變更。 如需隱藏環境處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專有**

### <a name="example"></a>範例

下列範例示範如何使用 *:::no-loc(argc):::* 、 *:::no-loc(argv):::* 和 *:::no-loc(envp):::* 引數來 `:::no-loc(main):::` 執行下列動作：

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (:::no-loc(argc)::: == 2) && _stricmp( :::no-loc(argv):::[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; :::no-loc(envp):::[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << :::no-loc(envp):::[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>剖析 c + + 命令列引數

**Microsoft 特定的**

當解讀作業系統命令列上指定的引數時，Microsoft C/c + + 啟動程式碼會使用下列規則：

- 引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。

- 插入號 :::no-loc(char)::: acter （^）不會被辨識為 escape :::no-loc(char)::: acter 或分隔符號。 :::no-loc(char):::Acter 是由作業系統中的命令列剖析器完整處理，然後才會傳遞至 `:::no-loc(argv):::` 程式中的陣列。

- 雙引號（"*string*"）括住的字串會被視為單一引數，不論中包含的空白字元為何。 有引號的字串可以內嵌到引數中。

- 前面加上反斜線（ \\ "）的雙引號會被視為常值的雙引號 :::no-loc(char)::: acter （"）。

- 反斜線會逐字解譯，除非後面緊接著雙引號。

- 如果雙引號後面加上偶數數目的反斜線，則會在每對反斜線的陣列中放入一個反斜線， `:::no-loc(argv):::` 並將雙引號轉譯為字串分隔符號。

- 如果雙引號後面加上奇數數目的反斜線，則會在每一對反斜線的陣列中放入一個反斜線， `:::no-loc(argv):::` 而雙引號會被重新加 :::no-loc(main)::: 上反斜線，使常值雙引號（"）放入中 `:::no-loc(argv):::` 。

### <a name="example"></a>範例

下列程式示範如何傳遞命令列引數：

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::,      // Number of strings in array :::no-loc(argv):::
          :::no-loc(char)::: *:::no-loc(argv):::[],   // Array of command-line argument strings
          :::no-loc(char)::: *:::no-loc(envp):::[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < :::no-loc(argc):::; count++ )
         cout << "  :::no-loc(argv):::[" << count << "]   "
                << :::no-loc(argv):::[count] << "\n";
}
```

下表顯示範例輸入和預期的輸出，示範上述清單中的規則。

### <a name="results-of-parsing-command-lines"></a>剖析命令列的結果

|命令列輸入|:::no-loc(argv):::[1]|:::no-loc(argv):::[2]|:::no-loc(argv):::第|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**結束 Microsoft 專有**

## <a name="wildcard-expansion"></a>萬用字元展開

**Microsoft 特定的**

您可以在命令列上使用問號 (?) 和星號 (*) 等萬用字元來指定檔案名稱和路徑引數。

命令列引數是由名為的常式 `_set:::no-loc(argv):::` （或 `_wset:::no-loc(argv):::` 在寬型 :::no-loc(char)::: acter 環境中）處理，預設不會將萬用字元展開為字串陣列中的個別字串 `:::no-loc(argv):::` 。 如需啟用萬用字元展開的詳細資訊，請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。

**結束 Microsoft 專有**

## <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理

**Microsoft 特定的**

如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 此常式會被呼叫 `_set:::no-loc(argv):::` ，並在[萬用字元展開](../cpp/wildcard-expansion.md)中說明。 若要隱藏其使用方式，請定義不在包含函式的檔案中執行任何工作的常式 `:::no-loc(main):::` ，並將其命名為 `_set:::no-loc(argv):::` 。 `_set:::no-loc(argv):::`您的定義會滿足的呼叫 `_set:::no-loc(argv):::` ，而且不會載入程式庫版本。

同樣地，如果您從未透過引數存取環境資料表 `:::no-loc(envp):::` ，您可以提供自己的空白常式來取代 `_set:::no-loc(envp):::` 環境處理常式。 就像函式一樣 `_set:::no-loc(argv):::` ， `_set:::no-loc(envp):::` 必須宣告為** :::no-loc(extern)::: "C"**。

您的程式可能會呼叫 `spawn` `exec` C 執行時間程式庫中的或系列常式。 如果有，您就不應該隱藏環境處理常式，因為此常式是用來將環境從父進程傳遞至子進程。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)
