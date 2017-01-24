---
title: "引數定義 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argc 引數"
  - "引數 [C++], main 函式的"
  - "argv 引數"
  - "envp 引數"
  - "main 函式, 引數"
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引數定義
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

原型中的引數  
  
```  
  
int main( int argc[ , char *argv[ ] [, char *envp[ ] ] ] ); int wmain( int argc[ , wchar_t *argv[ ] [, wchar_t *envp[ ] ] ] );  
```  
  
 允許使用方便命令列剖析的引數，同時可選擇性地存取環境變數。  引數定義如下：  
  
 `argc`  
 包含 `argv` 之後引數的計數。  `argc` 參數永遠會大於或等於 1。  
  
 `argv`  
 以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。  依照慣例，`argv`**\[0\]** 是對程式叫用的命令，`argv`**\[1\]** 是第一個命令列引數，依此類推，直到 `argv`**\[**`argc`**\]**，其永遠為 **NULL**。  如需隱藏命令列處理的詳細資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。  
  
 第一個命令列引數一定是 `argv`**\[1\]**，而最後一個會是 `argv`**\[**`argc` – 1**\]**。  
  
> [!NOTE]
>  依照慣例，`argv`**\[0\]** 是對程式叫用的命令。不過，您可以使用 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) 繁衍 \(Spawn\) 處理序，而如果您同時使用第一個和第二個引數 \(`lpApplicationName` 和 `lpCommandLine`\)，`argv`**\[0\]** 可能不是可執行檔名稱，請使用 [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) 擷取可執行檔名稱及其完整檔案路徑。  
  
## Microsoft 特定的  
 `envp`  
 `envp` 陣列 \(許多 UNIX 系統中常見的擴充功能\) 可用於 Microsoft C\+\+。  它是一個字串的陣列，表示在使用者的環境中設定的變數。  這個陣列由 **NULL** 項目終止。  它可以宣告為 **char \(char** \*envp\[ \]**\)** 的指標陣列，或宣告為 **char \(char** \*\*envp**\)** 指標的指標。  如果您的程式使用 **wmain** 而非 **main**，請使用 `wchar_t` 資料類型而不是 `char`。  傳遞至 **main** 和 **wmain** 的環境區塊是目前環境的「凍結」複本。  如果您後續透過呼叫 **putenv** 或 `_wputenv` 變更環境，則目前環境 \(如 `getenv`\/`_wgetenv` 和 `_environ`\/ `_wenviron` 變數所傳回\) 將會變更，不過 envp 所指向的區塊不會變更。  如需隱藏環境處理的詳細資訊，請參閱[自訂命令列處理](../cpp/customizing-cpp-command-line-processing.md)。  此引數在 C 中可與 ANSI 相容，但是在 C\+\+ 中則不相容。  
  
## END Microsoft 特定的  
  
## 範例  
 下列範例顯示如何使用 **main** 的 `argc`、`argv` 和 `envp` 引數：  
  
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
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)