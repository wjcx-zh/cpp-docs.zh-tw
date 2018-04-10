---
title: 剖析 c + + 命令列引數 |Microsoft 文件
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
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58db951b2c9459eb9511e0a354e1daec4b29b53d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="parsing-c-command-line-arguments"></a>剖析 C++ 命令列引數
**Microsoft 特定的**  
  
 Microsoft C/c + + 啟始程式碼在解譯作業系統命令列上指定的引數時會使用下列規則：  
  
-   引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。  
  
-   插入號字元 (^) 不會被辨識為逸出字元或分隔符號。 字元由完整作業系統中的命令列剖析器才能傳遞至`argv`程式中的陣列。  
  
-   以雙引號括住的字串 ("*字串*」) 會解譯為單一引數，不論內包含空白字元。 有引號的字串可以內嵌到引數中。  
  
-   前面有反斜線 (\\") 的雙引號會解譯為常值雙引號字元 (")。  
  
-   反斜線會逐字解譯，除非後面緊接著雙引號。  
  
-   如果雙引號後面反斜線為偶數，一個反斜線會置於`argv`一對反斜線，和雙引號的陣列會被解譯為字串分隔符號。  
  
-   如果雙引號後面奇數個反斜線，有一個反斜線會置於`argv`一對反斜線，和雙引號的陣列會 「 由逸出"剩餘的反斜線，導致常值雙引號 (") 放入`argv`。  
  
## <a name="example"></a>範例  
 下列程式會示範如何在命令列引數會傳遞：  
  
```  
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
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)