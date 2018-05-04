---
title: C/c + + 建置參考 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d26f729f660b3e51677303bb91b99e665a1a950
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cc-building-reference"></a>C/C++ 建置參考
Visual c + + 提供兩種建置 C/c + + 程式。 最簡單的 （且最常見的） 方法是[Visual c + + 開發環境中建置](../../ide/building-cpp-projects-in-visual-studio.md)。 其他的方式是[命令提示字元使用命令列工具來建立](../../build/building-on-the-command-line.md)。 在任一情況下，您可以建立使用 Visual c + + 原始程式碼編輯器或您選擇的第三方編輯器的原始程式檔。  
  
 如果您的程式使用 makefile，而不是.vcxproj 檔案，您可以仍會建置它做為開發環境中[外部專案](../../ide/building-external-projects.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [編譯 C/C++ 程式](../../build/reference/compiling-a-c-cpp-program.md)  
 請描述編譯器中，建立目的檔包含機器碼、 連結器指示詞、 區段、 外部參考，以及函式/資料的名稱。  
  
 [連結](../../build/reference/linking.md)  
 描述連結器，其結合了程式碼編譯器所建立的物件檔和靜態連結程式庫，解析名稱參考，並建立可執行檔。  
  
 [發行組建](../../build/reference/release-builds.md)  
 顯示有關您為何和何時要將偵錯建置為發行組建，並也會討論一些您在偵錯從變更的發行組建時可能會遇到的問題。  
  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)  
 提供主題連結，討論最佳化程式碼的機制：  
  
 [C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)  
 提供下列的命令列工具來檢視或操作組建輸出：  
  
 [C/C++ 建置錯誤](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 導入了目錄資料表中的建置錯誤區段。  
  
## <a name="related-sections"></a>相關章節  
 [C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)  
 討論的前置處理器準備進行編譯器的原始程式檔凙巨集、 運算子和指示詞。  
  
 [了解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)  
 討論自訂建置處理序。  
  
 [建置 C/c + + 程式](../../build/building-c-cpp-programs.md)  
 提供描述如何從命令列或 Visual Studio 整合式開發環境建置程式等主題的連結。  
  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)  
 說明在開發環境中，或在命令列上，設定編譯器選項。  
  
 [編譯器選項](../../build/reference/compiler-options.md)  
 提供主題連結，討論使用的編譯器選項。  
  
 [設定連結器選項](../../build/reference/setting-linker-options.md)  
 描述內部或外部的整合式的開發環境設定連結器選項。  
  
 [連結器選項](../../build/reference/linker-options.md)  
 提供主題連結，討論使用連結器選項。  
  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)  
 描述 Microsoft 瀏覽資訊維護公用程式 (BSCMAKE。EXE) 的瀏覽資訊檔 (.bsc)，從建置.sbr 編譯期間建立的檔案。  
  
 [LIB 參考](../../build/reference/lib-reference.md)  
 描述 Microsoft 的程式庫管理員 (LIB.exe)，建立並管理通用物件檔案格式 (COFF) 物件檔案的程式庫。  
  
 [EDITBIN 參考](../../build/reference/editbin-reference.md)  
 描述 Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE)，這麼做會修改通用物件檔案格式 (COFF) 的二進位檔案。  
  
 [DUMPBIN 參考](../../build/reference/dumpbin-reference.md)  
 描述 Microsoft COFF 二進位檔傾印工具 (DUMPBIN。EXE)，可顯示通用物件檔案格式 (COFF) 的二進位檔案的相關資訊。  
  
 [NMAKE 參考](../../build/nmake-reference.md)  
 描述 Microsoft Program Maintenance Utility (NMAKE。這是一種工具，建置專案 EXE)，根據描述檔案中包含的命令。