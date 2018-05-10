---
title: '#include 指示詞 （C/c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#include'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64cd6098f7a539fd883a9c8e0e0c116590a2f38f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="include-directive-cc"></a>#include 指示詞 (C/C++)
指示前置處理器，將指定之檔案的內容當做已在指示詞出現之處出現於原始程式中一般來處理。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #include  "path-spec"  
#include  <path-spec>  
```  
  
## <a name="remarks"></a>備註  
 您可以將常數和巨集定義組織在 Include 檔中，然後使用 `#include` 指示詞將這些定義加入至任何原始程式檔。 Include 檔對結合外部變數及複雜資料類型的宣告也很有用。 這些類型只可在針對該目的所建立的 Include 檔中定義和命名一次。  
  
 `path-spec` 是可選擇性在前面加上目錄規格的檔案名稱。 檔案名稱必須指定現有的檔案名稱。 `path-spec` 的語法取決於進行程式編譯的作業系統。  
  
 如需有關如何在 c + + 應用程式中使用編譯的組件的參考資訊[/clr](../build/reference/clr-common-language-runtime-compilation.md)，請參閱[#using](../preprocessor/hash-using-directive-cpp.md)。  
  
 這兩種語法形式都會導致該指示詞由指定之 Include 檔的整個內容所取代。 兩個形式之間的差異在於路徑未完整指定時，前置處理器搜尋標頭檔的順序。 下表顯示這兩種語法形式之間的差異。  
  
|語法形式|動作|  
|-----------------|------------|  
|有引號的形式|前置處理器會依此順序搜尋 Include 檔：<br /><br /> 1） 中包含的檔案相同的目錄`#include`陳述式。<br /><br /> 2） 在目錄中的目前開啟 include 檔，已開啟它們的順序相反。 搜尋會從 Include 檔的父目錄開始，並向上繼續搜尋所有上層 Include 檔的目錄。<br /><br /> 3） 沿著每個 /I 編譯器選項所指定的路徑。<br /><br /> 4)<br /><br /> 依循 INCLUDE 環境變數所指定的路徑。|  
|角括弧形式|前置處理器會依此順序搜尋 Include 檔：<br /><br /> 1） 沿著每個 /I 編譯器選項所指定的路徑。<br /><br /> 2） 當編譯就會發生在命令列，沿著由 INCLUDE 環境變數所指定的路徑。|  
  
 前置處理器只要找到具有指定名稱的檔案，就會立即停止搜尋。 如果您以雙引號 (" ") 括住 Include 檔完整明確的路徑規格，前置處理器只會搜尋該路徑規格並忽略標準目錄。  
  
 如果以雙引號括住的檔案名稱是不完整的路徑規格，前置處理器會先搜尋「父」檔案的目錄。 父檔案是包含 `#include` 指示詞的檔案。 例如，如果您在名為 `file2` 的檔案內包含名為 `file1` 的檔案，則 `file1` 為父檔案。  
  
 Include 檔可以是「巢狀」；也就是，`#include` 指示詞可以出現在另一個以 `#include` 指示詞命名的檔案中。 例如，`file2` 可以包含 `file3`。 在這種情況下，`file1` 仍將是 `file2` 的父代，但會是 `file3` 的「上二層」。  
  
 當 Include 檔形成巢狀包含時，以及在命令列進行編譯時，目錄搜尋會先從父檔案的目錄開始，繼續進行到所有上層檔案的目錄。 也就是說，搜尋會相對於包含目前處理中原始檔的目錄開始進行。 如果找不到檔案，則搜尋會移至 /I 編譯器選項指定的目錄。 最後，搜尋 INCLUDE 環境變數所指定的目錄。  
  
 在開發環境中，會忽略 INCLUDE 環境變數。 如需有關如何設定搜尋 include 檔的目錄資訊，這也適用於 LIB 環境變數，請參閱[VC + + 目錄屬性頁](../ide/vcpp-directories-property-page.md)。  
  
 此範例使用角括弧示範檔案包含：  
  
```  
#include <stdio.h>  
```  
  
 這個範例會將名為 STDIO.H 之檔案的內容加入至來源程式。 角括弧會讓前置處理器在搜尋 /I 編譯器選項指定的目錄之後，搜尋 STDIO.H 的 INCLUDE 環境變數所指定的目錄。  
  
 下一個範例使用引號形式示範檔案包含：  
  
```  
#include "defs.h"  
```  
  
 這個範例會將 DEFS.H 所指定之檔案的內容加入至來源程式。 引號表示前置處理器會先搜尋包含父原始程式檔的目錄。  
  
 Include 檔的巢狀可以擴充到最多 10 層。 處理巢狀 `#include` 後，前置處理器會繼續將封入 Include 檔插入原來的原始程式檔中。  
  
 **Microsoft 特定的**  
  
 為了尋找可包含的原始程式檔，前置處理器會先搜尋 /I 編譯器選項指定的目錄。 如果 /I 選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數，在角括號內尋找任何 Include 檔。 INCLUDE 環境變數和 /I 編譯器選項可以包含多個以分號 (;) 分隔的路徑。 如果多個目錄出現在 /I 選項中或在 INCLUDE 環境變數中，前置處理器會以其出現的順序搜尋它們。  
  
 例如，命令  
  
```  
CL /ID:\MSVC\INCLUDE MYPROG.C  
```  
  
 造成前置處理器在目錄 D:\MSVC\INCLUDE\ 中搜尋 Include 檔，例如 STDIO.H。 命令  
  
```  
SET INCLUDE=D:\MSVC\INCLUDE  
CL MYPROG.C  
```  
  
 有相同的效果。 如果兩個搜尋集合失敗，就會產生嚴重編譯器錯誤。  
  
 如果 Include 檔的完整指定檔案名稱為包含冒號的路徑 (例如，F:\MSVC\SPECIAL\INCL\TEST.H)，前置處理器會依循路徑執行。  
  
 Include 檔指定為`#include`"`path-spec`"，目錄搜尋會以父檔案的目錄開始，然後繼續進行到其上二層檔案的目錄。 也就是說，搜尋會相對於包含處理中原始程式檔 (內含 `#include` 指示詞) 的目錄開始進行。 如果沒有上二層檔案，也找不到此檔案，則會繼續搜尋，如同以角括弧括住了檔案名稱一般。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)