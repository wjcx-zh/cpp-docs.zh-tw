---
title: 引數定義
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: aebd4800ad8d653d532708784ef0a5333211d46b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857654"
---
# <a name="argument-definitions"></a>引數定義

原型中的引數

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

允許使用方便命令列剖析的引數，同時可選擇性地存取環境變數。 引數定義如下：

*argc*<br/>
包含*argv*中後面的引數計數的整數。 *Argc*參數一律大於或等於1。

*argv*<br/>
以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例，`argv[0]` 是用來叫用程式的命令，`argv[1]` 是第一個命令列引數，依此類推，直到 `argv[argc]`，這一律為 Null。 如需隱藏命令列處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。

第一個命令列引數一定是 `argv[1]`，而最後一個是 `argv[argc - 1]`。

> [!NOTE]
> 依照慣例，`argv[0]` 是用來叫用程式的命令。  不過，您可以使用[CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)來產生進程，而且如果您同時使用第一個和第二個引數（*lpApplicationName*和*lpCommandLine*），`argv[0]` 可能不是可執行檔名稱;使用[GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)來取出可執行檔名稱及其完整路徑。

**Microsoft 專屬**

*envp*<br/>
在許多 UNIX 系統中， *envp*陣列是通用的延伸模組，可在 Microsoft C++中使用。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列由 NULL 項目終止。 它可以宣告為**char** （`char *envp[]`）指標的陣列，或宣告為**char** （`char **envp`）指標的指標。 如果您的程式使用 `wmain` 而不是 `main`，請使用**wchar_t**資料類型，而不是**char**。 傳遞至 `main` 的環境區塊，`wmain` 是目前環境的「凍結」複本。 如果您後續透過呼叫 `putenv` 或 `_wputenv`來變更環境，則目前環境（如 `getenv` 或 `_wgetenv` 和 `_environ` 或 `_wenviron` 變數所傳回）將會變更，但 envp 所指向的區塊不會變更。 如需隱藏環境處理的相關資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專屬**

## <a name="example"></a>範例

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

## <a name="see-also"></a>請參閱

[main：程式啟動](../cpp/main-program-startup.md)