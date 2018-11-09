---
title: 包含有括號的檔案名稱
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: ddca97f6e40a9a64d809cd39c2e810890844a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555684"
---
# <a name="including-bracketed-filenames"></a>包含有括號的檔案名稱

**ANSI 3.8.2**：尋找可包含原始程式檔的方法

對於以角括弧括住的檔案規格，前置處理器不會搜尋父檔案的目錄。 「父」檔案是其中具有 [#include](../preprocessor/hash-include-directive-c-cpp.md) 指示詞的檔案。 相反地，它會開始搜尋在編譯器命令列上 /I 後方指定之目錄中的檔案。 如果 /I 選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數，在角括號內尋找任何 Include 檔。 INCLUDE 環境變數可以包含多個以分號 (**;**) 分隔的路徑。 如果多個目錄出現在 /I 選項中或在 INCLUDE 環境變數中，前置處理器會以其出現的順序搜尋它們。

## <a name="see-also"></a>請參閱

[前置處理指示詞](../c-language/preprocessing-directives.md)