---
title: 如何： 啟用 IntelliSense Makefile 專案 |Microsoft 文件
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
ms.openlocfilehash: 9de79d56c6e8b6e496c0e7988ada07ed7595ea70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>如何：在 Makefile 專案中啟用 IntelliSense
不正確地設定某些專案設定或編譯器選項時，Visual c + + makefile 專案在 IDE 中運作的 IntelliSense 會失敗。 若要設定 Visual c + + makefile 專案中，使用此程序，使 IntelliSense 可在 Visual Studio 開發環境中未開啟 makefile 專案。  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>若要啟用 makefile 專案，在 IDE 中的 IntelliSense  
  
1.  開啟**屬性頁** 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  選取**NMake**屬性頁面，然後再修改下方屬性**IntelliSense**依適當情況。  
  
    -   設定**前置處理器定義**makefile 專案中定義任何前置處理器符號的屬性。 請參閱[/D （前置處理器定義）](../build/reference/d-preprocessor-definitions.md)，如需詳細資訊。  
  
    -   設定**包含搜尋路徑**屬性，以指定的編譯器會搜尋以解析傳遞至 makefile 專案中的前置處理器指示詞的檔案參考的目錄清單。 請參閱[（其他 Include 目錄） /I](../build/reference/i-additional-include-directories.md)，如需詳細資訊。  
  
         使用 CL 所建置的專案。設定命令視窗中，從 EXE **INCLUDE**環境變數來指定編譯器要搜尋以解析傳遞至 makefile 專案中的前置處理器指示詞的檔案參考的目錄。  
  
    -   設定**強制包含**屬性，以指定的標頭檔至處理序，建置 makefile 專案時。 請參閱[/FI （命名強制包含檔案）](../build/reference/fi-name-forced-include-file.md)，如需詳細資訊。  
  
    -   設定**組件搜尋路徑**屬性，以指定的編譯器會搜尋來解析參考至您的專案中的.NET 組件的目錄清單。 請參閱[/AI （指定中繼資料目錄）](../build/reference/ai-specify-metadata-directories.md)，如需詳細資訊。  
  
    -   設定**強制使用組件**屬性來指定建置 makefile 專案時要處理的.NET 組件。 請參閱[/FU (命名強制 #using 檔案)](../build/reference/fu-name-forced-hash-using-file.md)，如需詳細資訊。  
  
    -   設定**其他選項**屬性來指定剖析 c + + 檔案時，Intellisense 所使用的其他編譯器參數。  
  
4.  按一下**確定**關閉屬性頁。  
  
5.  使用**全部儲存**命令，以儲存修改過的專案設定。  
  
 下次您開啟 makefile 專案在 Visual Studio 開發環境中，執行**清除方案**命令，然後**建置方案**makefile 專案命令。 IntelliSense 在 IDE 中正常運作。  
  
## <a name="see-also"></a>另請參閱  
 [使用 IntelliSense](/visualstudio/ide/using-intellisense)   
 [NMAKE 參考](../build/nmake-reference.md)   
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)