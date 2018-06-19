---
title: 剖析 C 命令列引數 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53b61bae046e73c4e49bbcaeb095b7bf230e95dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388597"
---
# <a name="parsing-c-command-line-arguments"></a>剖析 C 命令列引數
**Microsoft 特定的**  
  
 Microsoft C 啟動程式碼在解譯作業系統命令列所指定的引數時會使用下列規則：  
  
-   引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。  
  
-   用雙引號括住的字串會被解譯成單一引數，不論其內是否包含空白字元。 有引號的字串可以內嵌到引數中。 請注意，插入號 (**^**) 不會被辨識為逸出字元或分隔符號。  
  
-   前面有反斜線 (**\\"**) 的雙引號會解譯為常值雙引號 (**"**)。  
  
-   反斜線會逐字解譯，除非後面緊接著雙引號。  
  
-   如果雙引號前面有偶數數目的反斜線，則會將每一對反斜線 (**\\\\**) 的其中一個反斜線 (**\\**) 放到 `argv` 陣列中，並將雙引號 (**"**) 解譯為字串分隔符號。  
  
-   如果雙引號前面有奇數數目的反斜線，則會將每一對反斜線 (**\\\\**) 的其中一個反斜線 (**\\**) 放到 `argv` 陣列中，並且將雙引號解譯為剩餘反斜線的逸出序列，導致在 `argv` 中加入常值雙引號 (**"**)。  
  
 這個清單示範數個命令列引數範例傳遞至 `argv` 的解譯結果，以說明上述規則。 第二、三和四欄所列的輸出取自清單之後的 ARGS.C 程式。  
  
|命令列輸入|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"a b c" d e`|`a b c`|`d`|`e`|  
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|  
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// Parsing_C_Commandline_args.c  
// ARGS.C illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
//  
  
#include <stdio.h>  
  
int main( int argc, // Number of strings in array argv  
 char *argv[],      // Array of command-line argument strings  
 char **envp )      // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf_s( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf_s( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.  
    printf_s( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf_s( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
## <a name="comments"></a>註解  
 此程式輸出的其中一個範例是：  
  
```  
Command-line arguments:  
  argv[0]   C:\MSC\TEST.EXE  
  
Environment variables:  
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE  
  
  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;  
  PROMPT=[$p]   
  TEMP=c:\tmp  
  TMP=c:\tmp  
  EDITORS=c:\binr  
  WINDIR=c:\nt        
```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [main 函式和程式執行](../c-language/main-function-and-program-execution.md)