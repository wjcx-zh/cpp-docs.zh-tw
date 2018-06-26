---
title: 如何：在 Makefile 專案中啟用 IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b9b11f04f1fe8d201d6d07ca5ed83f9ca7d991b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705458"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>如何：在 Makefile 專案中啟用 IntelliSense
不正確地設定某些專案設定或編譯器選項時，Visual C++ makefile 專案的 IntelliSense 在 IDE 中會無法運作。 使用此程序設定 Visual C++ makefile 專案，使得在 Visual Studio 開發環境中開啟 makefile 專案時，IntelliSense 可以運作。  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>在 IDE 中啟用 makefile 專案的 IntelliSense  
  
1.  開啟 [屬性頁] 對話方塊。 如需詳細資料，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
2.  展開 [組態屬性] 節點。  
  
3.  選取 [NMake] 屬性頁，然後依適當情況修改 **IntelliSense** 下方屬性。  
  
    -   設定 [前置處理器定義] 屬性，在 makefile 專案中定義任何前置處理器符號。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。  
  
    -   設定 [包含搜尋路徑] 屬性，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](../build/reference/i-additional-include-directories.md)。  
  
         對於使用 CL.EXE 從命令視窗建置的專案，設定 **INCLUDE** 環境變數，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。  
  
    -   設定 [強制包含] 屬性，以指定在建置 makefile 專案時，要處理的標頭檔。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](../build/reference/fi-name-forced-include-file.md)。  
  
    -   設定 [組件搜尋路徑] 屬性，指定編譯器會搜尋的目錄清單，以便解析對您專案中 .NET 組件的參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。  
  
    -   設定 [強制使用組件] 屬性，以指定在建置 makefile 專案時，要處理的 .NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
    -   設定 [其他選項] 屬性，指定在剖析 C++ 檔案時，IntelliSense 要使用的其他編譯器參數。  
  
4.  按一下 [確定] 關閉屬性頁。  
  
5.  使用 [全部儲存] 命令，儲存修改過的專案設定。  
  
 下次您在 Visual Studio 開發環境中開啟 makefile 專案，對您的 makefile 專案執行 [清除方案] 命令，然後執行 [建置方案] 命令。 IntelliSense 應該在 IDE 中正常運作。  
  
## <a name="see-also"></a>請參閱  
 [使用 IntelliSense](/visualstudio/ide/using-intellisense)   
 [NMAKE 參考](../build/nmake-reference.md)   
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)