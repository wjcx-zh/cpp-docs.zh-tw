---
title: 剖析 c + + 命令列引數 |Microsoft Docs
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
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eca85baea71052525d70c90ac521ef5fa95a5118
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409203"
---
# <a name="parsing-c-command-line-arguments"></a>剖析 C++ 命令列引數
**Microsoft 專屬**  
  
 在解譯作業系統命令列上指定的引數時，Microsoft C/c + + 啟動程式碼會使用下列規則：  
  
-   引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。  
  
-   插入號字元 (^) 不會被辨識為逸出字元或分隔符號。 字元由完整作業系統中的命令列剖析器才會傳遞至`argv`程式中的陣列。  
  
-   以雙引號括住的字串 ("*字串*」) 會解譯為單一引數，不論內含的泛空白字元。 有引號的字串可以內嵌到引數中。  
  
-   前面有反斜線 (\\") 的雙引號會解譯為常值雙引號字元 (")。  
  
-   反斜線會逐字解譯，除非後面緊接著雙引號。  
  
-   如果雙引號後面偶數數目的反斜線，有一個反斜線會置於`argv`陣列中的每對反斜線，並將雙引號解譯為字串分隔符號。  
  
-   如果奇數數目的反斜線後面跟著雙引號，一個反斜線會放在`argv`陣列中的每對反斜線，並將雙引號 「 逸出 」 其餘的反斜線，並導致常值雙引號 (") 放入`argv`。  
  
## <a name="example"></a>範例  
 下列程式會示範如何在命令列引數會傳遞：  
  
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
  
 下表顯示範例輸入和預期的輸出，來示範上述清單中的規則。  
  
### <a name="results-of-parsing-command-lines"></a>剖析命令列的結果  
  
|命令列輸入|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"abc" d e`|`abc`|`d`|`e`|  
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)