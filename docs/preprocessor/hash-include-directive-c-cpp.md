---
title: '#include 指示詞 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 0792f522427e5658de992969745878894fbd454d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220256"
---
# <a name="include-directive-cc"></a>#include 指示詞 (CC++/)

指示前置處理器，將指定之檔案的內容當做已在指示詞出現之處出現於原始程式中一般來處理。

## <a name="syntax"></a>語法

> **#include**「*路徑規格*」 \
> **#include** *路徑-規格* \<>

## <a name="remarks"></a>備註

您可以將常數和巨集定義組織成 include 檔案, 然後使用 **#include**指示詞將它們新增至任何原始程式檔。 Include 檔對結合外部變數及複雜資料類型的宣告也很有用。 這些類型只可在針對該目的所建立的 Include 檔中定義和命名一次。

*路徑規格*是一個檔案名, 可以選擇性地在前面加上目錄規格。 檔案名稱必須指定現有的檔案名稱。 *路徑規格*的語法取決於程式編譯所在的作業系統。

如需如何在使用C++ [/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯的應用程式中參考元件的詳細資訊, 請參閱[#using](../preprocessor/hash-using-directive-cpp.md)。

這兩種語法形式都會導致該指示詞由指定之 Include 檔的整個內容所取代。 兩個形式之間的差異在於路徑未完整指定時，前置處理器搜尋標頭檔的順序。 下表顯示這兩種語法形式之間的差異。

|語法形式|動作|
|---|------------|
|有引號的形式|前置處理器會依此順序搜尋 Include 檔：<br/><br/> 1) 與包含 **#include**語句的檔案位於相同的目錄中。<br/><br/> 2) 在目前開啟的 include 檔案目錄中, 以其開啟的相反順序排列。 搜尋會從 Include 檔的父目錄開始，並向上繼續搜尋所有上層 Include 檔的目錄。<br/><br/> 3) 沿著每個 **/i**編譯器選項所指定的路徑。<br/><br/> 4) 沿著 INCLUDE 環境變數所指定的路徑。|
|角括弧形式|前置處理器會依此順序搜尋 Include 檔：<br/><br/> 1) 沿著每個 **/i**編譯器選項所指定的路徑。<br/><br/> 2) 在命令列上進行編譯時, 沿著 INCLUDE 環境變數所指定的路徑。|

前置處理器只要找到具有指定名稱的檔案，就會立即停止搜尋。 如果您在雙引號 (`" "`) 之間括住 include 檔案的完整明確路徑規格, 預處理器只會搜尋該路徑規格並忽略標準目錄。

如果以雙引號括住的檔案名稱是不完整的路徑規格，前置處理器會先搜尋「父」檔案的目錄。 父檔案是包含 **#include**指示詞的檔案。 例如, 如果您在名為*file1*的檔案中包含名為*file2*的檔案, *file1*就是父檔案。

Include 檔案可以「nested」: **#Include**指示詞可能會出現在另一個 **#include**指示詞所命名的檔案中。 例如, *file2*可能包含*file3*。 在此情況下, *file1*仍然是*file2*的父系, 但它會是*file3*的「祖系」。

當 include 檔是已嵌套的, 而且在命令列上進行編譯時, 目錄搜尋會從父檔案的目錄開始。 然後, 它會繼續執行任何祖系檔案的目錄。 也就是說，搜尋會相對於包含目前處理中原始檔的目錄開始進行。 如果找不到檔案, 搜尋就會移至 [ [/i (其他 include 目錄)](../build/reference/i-additional-include-directories.md) ] 編譯器選項所指定的目錄。 最後，搜尋 INCLUDE 環境變數所指定的目錄。

從 Visual Studio 開發環境中, 會忽略 INCLUDE 環境變數。 如需如何設定搜尋包含檔案和程式庫檔案之目錄的詳細資訊, 請參閱[VC + + 目錄屬性頁](../build/reference/vcpp-directories-property-page.md)。

此範例使用角括弧示範檔案包含：

```C
#include <stdio.h>
```

這個範例會將名為 STDIO.H 之檔案的內容加入至來源程式。 角括弧會使預處理器搜尋包含環境變數所指定的目錄, 以進行 STDIO.H。H, 在搜尋 **/i**編譯器選項所指定的目錄之後。

下一個範例使用引號形式示範檔案包含：

```C
#include "defs.h"
```

這個範例會將 DEFS.H 所指定之檔案的內容加入至來源程式。 引號表示前置處理器會先搜尋包含父原始程式檔的目錄。

Include 檔的巢狀可以擴充到最多 10 層。 處理嵌套的 **#include**時, 預處理器會繼續將內含的 include 檔案插入原始來源檔案中。

**Microsoft 專屬**

為了找出可包含原始程式檔, 預處理器會先搜尋 **/i**編譯器選項所指定的目錄。 如果 **/i**選項不存在, 或失敗, 則預處理器會使用 INCLUDE 環境變數, 在角括弧內尋找任何 INCLUDE 檔案。 INCLUDE 環境變數和 **/i**編譯器選項可以包含多個路徑, 並以分號 ( **;** ) 分隔。 如果一個以上的目錄出現在 **/i**選項或 INCLUDE 環境變數中, 則預處理器會依其出現的順序進行搜尋。

例如，命令

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

造成前置處理器在目錄 D:\MSVC\INCLUDE\ 中搜尋 Include 檔，例如 STDIO.H。 命令

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

有相同的效果。 如果兩個搜尋集合失敗，就會產生嚴重編譯器錯誤。

如果 Include 檔的完整指定檔案名稱為包含冒號的路徑 (例如，F:\MSVC\SPECIAL\INCL\TEST.H)，前置處理器會依循路徑執行。

針對指定為`#include "path-spec"`的 include 檔案, 目錄搜尋會從父檔案的目錄開始, 然後繼續進行任何祖系檔案的目錄。 也就是說, 搜尋會開始相對於包含要處理之 **#include**指示詞的來源檔案的目錄。 如果沒有上二層檔案，也找不到此檔案，則會繼續搜尋，如同以角括弧括住了檔案名稱一般。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)\
[/I (其他 include 目錄)](../build/reference/i-additional-include-directories.md)
