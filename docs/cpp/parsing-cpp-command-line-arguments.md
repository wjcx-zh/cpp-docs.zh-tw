---
title: "剖析 C++ 命令列引數 | Microsoft Docs"
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
  - "引號，命令列引數"
  - "雙引號"
  - "命令列剖析"
  - "剖析命令列引數"
  - "啟始程式碼剖析命令列引數"
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剖析 C++ 命令列引數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 Microsoft C/c + + 啟始程式碼在解譯作業系統命令列上指定的引數時會使用下列規則︰  
  
-   引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。  
  
-   插入號字元 (^) 無法辨識為逸出字元或分隔符號。 字元由完全在作業系統中的命令列剖析再傳遞給 `argv` 程式中的陣列。  
  
-   以雙引號括住的字串 ("*字串*」) 會解譯為單一引數，不論其內是否包含泛空白字元。 有引號的字串可以內嵌到引數中。  
  
-   雙引號前面有反斜線 (\\」) 會解譯為常值雙引號字元 （"）。  
  
-   反斜線會逐字解譯，除非後面緊接著雙引號。  
  
-   如果偶數數目的反斜線後面接著雙引號，有一個反斜線會置於 `argv` 陣列中的每一對反斜線，並將雙引號解譯為字串分隔符號。  
  
-   如果奇數數目的反斜線後面接著雙引號，有一個反斜線會置於 `argv` 陣列中的每一對反斜線，並將雙引號 「 逸出 」 所剩餘的反斜線，導致常值雙引號 （"），放在 `argv`。  
  
## <a name="example"></a>範例  
 下列程式將示範如何在命令列引數會傳遞︰  
  
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
  
|命令列輸入|argv[1]|argv [2]|argv [3]|  
|-------------------------|---------------|---------------|---------------|  
|`"abc" d e`|`abc`|`d`|`e`|  
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="end-microsoft-specific"></a>END Microsoft 特定的  
  
## <a name="see-also"></a>另請參閱  
 [main︰ 程式啟動](../cpp/main-program-startup.md)