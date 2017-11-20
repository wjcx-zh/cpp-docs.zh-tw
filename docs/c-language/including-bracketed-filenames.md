---
title: "包含有括號的檔案名稱 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f118417a7ed2fdf8cad77775e144b81655c56916
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="including-bracketed-filenames"></a>包含有括號的檔案名稱
**ANSI 3.8.2**：尋找可包含原始程式檔的方法  
  
 對於以角括弧括住的檔案規格，前置處理器不會搜尋父檔案的目錄。 「父」檔案是其中具有 [#include](../preprocessor/hash-include-directive-c-cpp.md) 指示詞的檔案。 相反地，它會開始搜尋在編譯器命令列上 /I 後方指定之目錄中的檔案。 如果 /I 選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數，在角括號內尋找任何 Include 檔。 INCLUDE 環境變數可以包含多個以分號 (**;**) 分隔的路徑。 如果多個目錄出現在 /I 選項中或在 INCLUDE 環境變數中，前置處理器會以其出現的順序搜尋它們。  
  
## <a name="see-also"></a>另請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)