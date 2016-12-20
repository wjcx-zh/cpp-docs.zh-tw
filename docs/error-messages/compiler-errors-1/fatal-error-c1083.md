---
title: "嚴重錯誤 C1083 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1083"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1083"
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1083
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟 filetype 檔案：'file' : 訊息  
  
 編譯器在找不到檔案時會產生 C1083 錯誤。 編譯器產生這個錯誤的常見原因如下。  
  
 **指定的檔案名稱有誤**  
  
 檔案名稱可能輸入錯誤。 例如：  
  
```cpp  
#include <algorithms.h>  
```  
  
 可能沒有找到您要的檔案。 確實有一個 Standard C++ 程式庫標頭檔名為 algorithms，但是沒有 .h 副檔名。 使用此 `include` 指示詞會找不到檔案。 若要修正此問題，請確認輸入的檔案名稱是正確的。  
  
 某些 C 執行階段程式庫標頭位於標準 Include 目錄的子目錄中。 例如，若要包含 sys\types.h，您必須在 include 指示詞中包含 sys 子目錄名稱：  
  
 `#include <sys\types.h>`  
  
 **檔案未包含在編譯器搜尋路徑**  
  
 編譯器無法使用 `include` 或 `import` 指示詞中指出的搜尋規則來找到檔案。 例如，如果標頭檔名稱是以引號括住  
  
 `#include "myincludefile.h"`  
  
 通知編譯器會先在含有原始程式檔的相同目錄中尋找檔案，然後才在建置環境指定的其他位置中尋找擋案。 如果引號中含有絕對路徑，則編譯器只會在該位置尋找檔案。 如果引號中含有相對路徑，則編譯器會在來源目錄相對的目錄中尋找檔案。 如果此名稱是以角括弧括住  
  
 `#include <stdio.h>`  
  
 編譯器會依循建置環境、 所定義的搜尋路徑 **/I** 編譯器選項 **/X** 編譯器選項和 **包含** 環境變數。 如需詳細資訊，包括用來尋找檔案，搜尋順序有關的特定詳細資料請參閱 [#include 指示詞 （C/c + +）](../../preprocessor/hash-include-directive-c-cpp.md) 和 [#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。  
  
 即使當標頭檔中所列 **方案總管] 中** 專案的一部分，檔案時，才找由編譯器所參考到 `include` 或 `import` 指示詞而且位於目錄搜尋路徑。 不同類型的組建可能會使用不同的搜尋路徑。  **/X** 編譯器選項可以用來排除於 include 檔搜尋路徑的目錄。 這樣可讓不同的組建使用同名但存放在不同目錄下的 Include 檔案。 這是除了使用前置處理器命令進行條件式編譯以外的另一種作法。 如需詳細資訊 **/X** 編譯器選項，請參閱 [/X （忽略標準 Include 路徑）](../../build/reference/x-ignore-standard-include-paths.md)。  
  
 在命令列叫用編譯器時，通常會使用環境變數指定搜尋路徑。 如果所描述的搜尋路徑 **包含** 環境變數設定不正確，就會產生 C1083 錯誤。 如需如何使用環境變數的詳細資訊，請參閱 [How to︰ 在組建中使用環境變數](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)。  
  
 若要修正此問題，請修正編譯器用來搜尋包含或匯入之檔案的路徑。 新專案會使用預設搜尋路徑。 您可能必須修改路徑以加入專案的目錄。 如果您在命令列上編譯，請設定 **包含** 環境變數或 **/I** 編譯器選項以指定的檔案路徑。 若要在 Visual Studio 中設定 include 目錄路徑，請開啟專案的 **屬性頁** 對話方塊方塊中，展開 **組態屬性** 和 **VC + + 目錄**, ，然後編輯 **Include 目錄** 值。 如需在 Visual Studio 編譯器所搜尋的每個使用者和每個專案目錄的詳細資訊，請參閱 [VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)。 如需詳細資訊 **/I** 編譯器選項，請參閱 [/I （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md)。  
  
 **就會包含檔案名稱的版本錯誤**  
  
 C1083 錯誤也可能表示包含了錯誤版本的檔案。 包含錯誤檔案版本的例子像是，組建包含的檔案在其 `include` 指示詞中參考了該組建不適用的標頭檔。 找不到標頭檔時，編譯器會產生 C1083 錯誤。 若要修正這個問題，請使用正確的檔案，而不是將標頭檔或目錄加入至組建中。  
  
 **先行編譯標頭檔未經先行**  
  
 當專案已設定為使用先行編譯標頭檔時，必須已建立相關的 .pch 檔案，才能編譯用到標頭內容的檔案。 例如，新 MFC 專案的專案目錄中會自動建立 stdafx.cpp 檔案。 請先編譯該檔案以建立先行編譯標頭檔  (在標準的建置程序設計中，這個動作會自動完成)。如需詳細資訊，請參閱 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)。  
  
 **其他的原因**  
  
-   此檔案會使用 managed 程式碼，但編譯器選項 **/clr** 未指定。 如需詳細資訊，請參閱 [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
-   檔案使用不同的編譯 **/analyze** 編譯器選項設定與用來先行編譯標頭。 (當專案的標頭中都會先行編譯時，應一律使用相同 **/analyze** 設定。)如需詳細資訊，請參閱 [/analyze （程式碼分析）](../../build/reference/analyze-code-analysis.md)。  
  
-   檔案、目錄或磁碟為唯讀。  
  
-   未被授與檔案或目錄的存取權限。  
  
-   檔案控制代碼不足。 請關閉部分應用程式，再重新編譯。 在一般情況下，這種狀況並不常見。 不過，在實體記憶體有限的電腦上建置大型專案時，有可能會發生這種狀況。  
  
 下列範例會產生 C1083 錯誤。  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"   // OK  
```  
  
 如何建置在 IDE 中或命令列上的 C/c + + 專案的相關資訊及設定環境變數的相關資訊，請參閱 [建置 C/c + + 程式](../../build/building-c-cpp-programs.md)。
 
 ## <a name="see-also"></a>請參閱
 [MSBuild 屬性](MSBuild%20Properties.md)