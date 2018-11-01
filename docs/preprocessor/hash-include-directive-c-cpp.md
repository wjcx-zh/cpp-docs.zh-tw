---
title: '#include 指示詞 （C/c + +）'
ms.date: 11/04/2016
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 3cf595fd8f519706f43ad70c4cdddf0297c8149e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492530"
---
# <a name="include-directive-cc"></a>#include 指示詞 (C/C++)
指示前置處理器，將指定之檔案的內容當做已在指示詞出現之處出現於原始程式中一般來處理。

## <a name="syntax"></a>語法

```
#include  "path-spec"
#include  <path-spec>
```

## <a name="remarks"></a>備註

您可以組織在 include 檔的常數和巨集的定義，然後使用 **#include**指示詞將它們新增到任何原始程式檔。 Include 檔對結合外部變數及複雜資料類型的宣告也很有用。 這些類型只可在針對該目的所建立的 Include 檔中定義和命名一次。

`path-spec` 是可選擇性在前面加上目錄規格的檔案名稱。 檔案名稱必須指定現有的檔案名稱。 `path-spec` 的語法取決於進行程式編譯的作業系統。

如需有關如何在 c + + 應用程式中使用編譯的組件的參考資訊[/clr](../build/reference/clr-common-language-runtime-compilation.md)，請參閱[#using](../preprocessor/hash-using-directive-cpp.md)。

這兩種語法形式都會導致該指示詞由指定之 Include 檔的整個內容所取代。 兩個形式之間的差異在於路徑未完整指定時，前置處理器搜尋標頭檔的順序。 下表顯示這兩種語法形式之間的差異。

|語法形式|動作|
|-----------------|------------|
|有引號的形式|前置處理器會依此順序搜尋 Include 檔：<br /><br /> 1） 中包含的檔案相同的目錄 **#include**陳述式。<br /><br /> 2） 在目前開啟的目錄包含檔案，它們已開啟的相反順序。 搜尋會從 Include 檔的父目錄開始，並向上繼續搜尋所有上層 Include 檔的目錄。<br /><br /> 3） 在路徑所指定的每個`/I`編譯器選項。<br /><br /> 4)<br /><br /> 依循 INCLUDE 環境變數所指定的路徑。|
|角括弧形式|前置處理器會依此順序搜尋 Include 檔：<br /><br /> 1） 在路徑所指定的每個`/I`編譯器選項。<br /><br /> 2） 進行編譯時在命令列上，沿著路徑所指定的 INCLUDE 環境變數。|

前置處理器只要找到具有指定名稱的檔案，就會立即停止搜尋。 如果您以雙引號 (" ") 括住 Include 檔完整明確的路徑規格，前置處理器只會搜尋該路徑規格並忽略標準目錄。

如果以雙引號括住的檔案名稱是不完整的路徑規格，前置處理器會先搜尋「父」檔案的目錄。 父檔案是檔案，其中包含 **#include**指示詞。 例如，如果您在名為 `file2` 的檔案內包含名為 `file1` 的檔案，則 `file1` 為父檔案。

Include 檔可以 「 巢狀 」;亦即 **#include**指示詞可以出現在另一個名為的檔案 **#include**指示詞。 例如，`file2` 可以包含 `file3`。 在這種情況下，`file1` 仍將是 `file2` 的父代，但會是 `file3` 的「上二層」。

當 Include 檔形成巢狀包含時，以及在命令列進行編譯時，目錄搜尋會先從父檔案的目錄開始，繼續進行到所有上層檔案的目錄。 也就是說，搜尋會相對於包含目前處理中原始檔的目錄開始進行。 如果找不到檔案，則搜尋會移至所指定的目錄`/I`編譯器選項。 最後，搜尋 INCLUDE 環境變數所指定的目錄。

在開發環境中，會忽略 INCLUDE 環境變數。 如需有關如何設定搜尋 include 檔的目錄資訊 — 這也適用於 LIB 環境變數，請參閱[VC + + Directories Property Page](../ide/vcpp-directories-property-page.md)。

此範例使用角括弧示範檔案包含：

```
#include <stdio.h>
```

這個範例會將名為 STDIO.H 之檔案的內容加入至來源程式。 角括號會造成前置處理器搜尋 STDIO INCLUDE 環境變數所指定的目錄。H，所指定的目錄之後，搜尋`/I`編譯器選項。

下一個範例使用引號形式示範檔案包含：

```
#include "defs.h"
```

這個範例會將 DEFS.H 所指定之檔案的內容加入至來源程式。 引號表示前置處理器會先搜尋包含父原始程式檔的目錄。

Include 檔的巢狀可以擴充到最多 10 層。 當巢狀 **#include**是處理，前置處理器會繼續將封入 include 檔插入原來的原始程式檔。

**Microsoft 專屬**

若要尋找可包含原始程式檔，前置處理器會先搜尋所指定的目錄`/I`編譯器選項。 如果`/I`選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數來尋找角括弧括住任何包含檔案。 INCLUDE 環境變數和`/I`編譯器選項可以包含多個路徑，並以分號 （;）。 如果多個目錄會顯示為一部分`/I`選項，或在 INCLUDE 環境變數中，前置處理器搜尋它們以其出現的順序。

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

Include 檔指定為`#include`"`path-spec`」，目錄搜尋父檔案的目錄開始，並繼續進行到所有上層檔案的目錄。 也就是搜尋開始包含來源檔案，其中包含目錄的相對 **#include**正在處理的指示詞。 如果沒有上二層檔案，也找不到此檔案，則會繼續搜尋，如同以角括弧括住了檔案名稱一般。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)