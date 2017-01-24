---
title: "include_alias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.include_alias"
  - "include_alias_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "include_alias pragma"
  - "Pragma, include_alias"
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# include_alias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 *short\_filename* 要做為 *long\_filename* 的別名使用。  
  
## 語法  
  
```  
  
      #pragma include_alias( "  
      long_filename  
      ", "  
      short_filename  
      " )  
#pragma include_alias( <long_filename>, <short_filename> )  
```  
  
## 備註  
 有些檔案系統可使用比 8.3 FAT 檔案系統所限制更長的標頭檔名稱。  由於較長標頭檔名稱的前八個字元不一定是唯一的，因此編譯器無法依照 8.3 的限制直接截斷較長的名稱。  只要編譯器遇到 *long\_filename* 字串，就會以 *short\_filename* 替代，並且改為尋找標頭檔 *short\_filename*。  這個 pragma 必須出現在對應的 `#include` 指示詞前面。  例如：  
  
```  
// First eight characters of these two files not unique.  
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )  
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )  
  
#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )  
  
#include "AppleSystemHeaderQuickdraw.h"  
#include "AppleSystemHeaderFruit.h"  
#include "GraphicsMenu.h"  
```  
  
 要搜尋的別名無論大小寫、拼字和雙引號或角括號的用法，都必須完全符合規格。  **include\_alias** pragma 會對檔案名稱進行簡單的字串比對，而不會再執行其他檔案名稱驗證。  例如，假設有下列指示詞：  
  
```  
#pragma include_alias("mymath.h", "math.h")  
#include "./mymath.h"  
#include "sys/mymath.h"  
```  
  
 不會設定別名 \(替代\)，因為標頭檔字串並非完全相符。  此外，不會替代做為 \/Yu 和 \/Yc 編譯器選項引數使用的標頭檔名稱，或 **hdrstop** pragma。  例如，如果原始程式檔包含下列指示詞：  
  
```  
#include <AppleSystemHeaderStop.h>  
```  
  
 則對應的編譯器選項應該是  
  
```  
/YcAppleSystemHeaderStop.h  
```  
  
 您可以使用 **include\_alias** pragma 將任一個標頭檔名稱對應到另一個。  例如：  
  
```  
#pragma include_alias( "api.h", "c:\version1.0\api.h" )  
#pragma include_alias( <stdio.h>, <newstdio.h> )  
#include "api.h"  
#include <stdio.h>  
```  
  
 請勿將使用雙引號含括的檔案名稱與使用角括號含括的檔案名稱混用。  例如，以上面兩個 **\#pragma include\_alias** 指示詞為例，編譯器不會對下列 `#include` 指示詞執行替代：  
  
```  
#include <api.h>  
#include "stdio.h"  
```  
  
 此外，下列指示詞會產生錯誤：  
  
```  
#pragma include_alias(<header.h>, "header.h")  // Error  
```  
  
 請注意，在錯誤訊息中或是做為預先定義之 **\_\_FILE\_\_** 巨集的值回報的檔案名稱，就是執行替代之後的檔案名稱。  例如，在下列指示詞後面：  
  
```  
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )  
#include "VeryLongFileName.H"  
```  
  
 VERYLONGFILENAME.H 中的錯誤會產生下列錯誤訊息：  
  
```  
myfile.h(15) : error C2059 : syntax error  
```  
  
 另請注意，目前不支援轉移。  假設有下列指示詞：  
  
```  
#pragma include_alias( "one.h", "two.h" )  
#pragma include_alias( "two.h", "three.h" )  
#include "one.h"  
```  
  
 編譯器會搜尋 TWO.H 這個檔案，而不是 THREE.H。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)