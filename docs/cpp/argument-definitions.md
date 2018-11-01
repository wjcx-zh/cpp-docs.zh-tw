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
ms.openlocfilehash: 3f194f337288f86190177fc7fa0f63bf18f45665
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444183"
---
# <a name="argument-definitions"></a>引數定義

原型中的引數

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

允許使用方便命令列剖析的引數，同時可選擇性地存取環境變數。 引數定義如下：

*argc*<br/>
整數，包含所遵循的引數的計數*argv*。 *Argc*參數一律是大於或等於 1。

*argv*<br/>
以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例， `argv` **[0]** 是叫用程式與命令`argv` **[1]** 是第一個命令列引數，並依此類推，直到`argv` **[**`argc`**]**，一律為 NULL。 請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)如需隱藏命令列處理的資訊。

第一個命令列引數一定是`argv` **[1]** 最後一個，而且`argv` **[** `argc` -1 **]**。

> [!NOTE]
>  依照慣例，`argv`**[0]** 是對程式叫用的命令。  不過，就可以繁衍 （spawn） 處理程序，使用[CreateProcess](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)如果您使用第一個和第二個引數 (*lpApplicationName*並*lpCommandLine*)， `argv`**[0]** 可能不是可執行檔名稱，請使用[GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)擷取可執行檔的名稱和其完整路徑。

## <a name="microsoft-specific"></a>Microsoft 特定的

*envp*<br/>
*Envp*陣列，這是常見的擴充功能，許多 UNIX 系統中，會在 Microsoft c + +。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列由 NULL 項目終止。 它可以宣告為陣列的指標**char (char** \*envp []**)** 或為指標的指標**char (char** \* \*envp **)**。 如果您的程式使用`wmain`而非`main`，使用`wchar_t`資料類型，而非**char**。 環境區塊傳遞給`main`和`wmain`是目前環境的 「 凍結 」 複本。 如果您接著變更環境中的，透過呼叫`putenv`或`_wputenv`，目前的環境 (所傳回的`getenv` / `_wgetenv`並`_environ` /  `_wenviron`變數) 將變更，不過 envp 所指向的區塊不會變更。 請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)如需隱藏環境處理的資訊。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專屬**

## <a name="example"></a>範例

下列範例示範如何使用*argc*， *argv*，並*envp*引數`main`:

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

## <a name="see-also"></a>另請參閱

[main：程式啟動](../cpp/main-program-startup.md)