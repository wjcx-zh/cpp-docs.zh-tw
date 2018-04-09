---
title: 引數定義 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d30dd0c58cd4967065ee3e3c3c4df9538ea194a0
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2018
---
# <a name="argument-definitions"></a>引數定義
原型中的引數  
  
```  
  
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);  
```  
  
 允許使用方便命令列剖析的引數，同時可選擇性地存取環境變數。 引數定義如下：  
  
 `argc`  
 包含 `argv` 之後引數的計數。 `argc` 參數永遠會大於或等於 1。  
  
 `argv`  
 以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。 依照慣例， `argv` **[0]**是叫用程式用的命令`argv` **[1]**是第一個命令列引數，並依此類推，直到`argv` **[**`argc`**]**，一律**NULL**。 請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)如需隱藏命令列處理的資訊。  
  
 第一個命令列引數一定是`argv` **[1]**並會在最後一個`argv` **[** `argc` -1**]**。  
  
> [!NOTE]
>  依照慣例，`argv`**[0]** 是對程式叫用的命令。  不過，它可能是繁衍 （spawn） 程序，使用[CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197)如果您使用第一個和第二個引數 (`lpApplicationName`和`lpCommandLine`)， `argv` **[0]**可能不是可執行檔的名稱。使用[GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197)擷取可執行檔名稱，而其完整路徑。  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `envp`  
 `envp` 陣列 (許多 UNIX 系統中常見的擴充功能) 可用於 Microsoft C++。 它是一個字串的陣列，表示在使用者的環境中設定的變數。 這個陣列會以結尾**NULL**項目。 它可以宣告為陣列的指標**char (char** \*envp []**)**或作為指標的指標**char (char** \* \*envp**)**。 如果您的程式使用**wmain**而不是**主要**，使用`wchar_t`資料類型，而不是`char`。 環境區塊傳遞至**主要**和**wmain**目前環境的 「 凍結 」 複本。 如果您後續又變更環境中的，透過呼叫**putenv**或`_wputenv`，目前的環境 (傳回`getenv` / `_wgetenv`和`_environ` /  `_wenviron`變數) 變更，不過 envp 所指向的區塊將不會變更。 請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)如需隱藏環境處理的資訊。 此引數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。  
  
**結束 Microsoft 特定的**  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`argc`， `argv`，和`envp`引數**主要**:  
  
```  
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