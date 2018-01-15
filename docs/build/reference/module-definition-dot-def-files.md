---
title: "模組定義 (。Def) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49f5eb5b75bad22b59cb4fbb98554bbfd44d13b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="module-definition-def-files"></a>模組定義檔案 (.Def)
模組定義 (.def) 檔會提供連結器匯出、 屬性和連結的程式的其他資訊的相關資訊。 建置 DLL 時，便最有用.def 檔。 因為有[連結器選項](../../build/reference/linker-options.md)可用而不是模組定義陳述式，.def 檔案通常不是必要。 您也可以使用[__declspec （dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md)做為指定的方式匯出的函式。  
  
 您可以使用連結器階段叫用.def 檔[/DEF （指定模組定義檔）](../../build/reference/def-specify-module-definition-file.md)連結器選項。  
  
 如果您要建置的.exe 檔案，沒有匯出，則使用.def 檔可以讓輸出檔案較大且更慢載入。  
  
 如需範例，請參閱[匯出從 DLL 使用.DEF 檔](../../build/exporting-from-a-dll-using-def-files.md)。  
  
 請參閱下列各節，如需詳細資訊：  
  
-   [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [名稱](../../build/reference/name-c-cpp.md)  
  
-   [區段](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [版本](../../build/reference/version-c-cpp.md)  
  
-   [保留的字](../../build/reference/reserved-words.md)  
  
## <a name="see-also"></a>請參閱  
 [C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [連結器選項](../../build/reference/linker-options.md)  