---
title: 包含有括號的檔案名稱 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba45c21029a428784e1c8410dcf42295aa6350f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383822"
---
# <a name="including-bracketed-filenames"></a>包含有括號的檔案名稱
**ANSI 3.8.2**：尋找可包含原始程式檔的方法  
  
 對於以角括弧括住的檔案規格，前置處理器不會搜尋父檔案的目錄。 「父」檔案是其中具有 [#include](../preprocessor/hash-include-directive-c-cpp.md) 指示詞的檔案。 相反地，它會開始搜尋在編譯器命令列上 /I 後方指定之目錄中的檔案。 如果 /I 選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數，在角括號內尋找任何 Include 檔。 INCLUDE 環境變數可以包含多個以分號 (**;**) 分隔的路徑。 如果多個目錄出現在 /I 選項中或在 INCLUDE 環境變數中，前置處理器會以其出現的順序搜尋它們。  
  
## <a name="see-also"></a>請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)