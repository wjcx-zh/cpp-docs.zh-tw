---
title: C/C++ 建置參考
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 36f261ee993932d1a08d5cdb02e2d4681ae60f0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481727"
---
# <a name="cc-building-reference"></a>C/C++ 建置參考

Visual c + + 提供兩種建置 C/c + + 程式。 最簡單 （且最常見） 的方式為： [Visual c + + 開發環境內建置](../../ide/building-cpp-projects-in-visual-studio.md)。 其他的方式為[命令提示字元使用命令列工具來建立](../../build/building-on-the-command-line.md)。 在任一情況下，您可以建立使用 Visual c + + 原始檔編輯器或您選擇的協力廠商編輯器的原始程式檔。

如果您的程式使用 makefile，而不是.vcxproj 檔案，您仍然以建置開發環境，做為[外部專案](../../ide/building-external-projects.md)。

## <a name="in-this-section"></a>本節內容

[編譯 C/C++ 程式](../../build/reference/compiling-a-c-cpp-program.md)<br/>
描述編譯器，這會建立包含機器碼，連結器指示詞、 區段、 外部參考，以及函式/資料名稱的物件檔案。

[連結](../../build/reference/linking.md)<br/>
說明連結器，其結合了來自編譯器所建立的物件檔案和靜態連結程式庫程式碼，會解析名稱的參考，並建立可執行檔。

[發行組建](../../build/reference/release-builds.md)<br/>
將資訊呈現在您為何和何時要將變更從 「 偵錯建置為發行組建，並也會討論的一些變更從 「 偵錯發行組建時，可能會遇到的問題。

[最佳化程式碼](../../build/reference/optimizing-your-code.md)<br/>
提供主題連結，討論最佳化程式碼的機制：

[C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)<br/>
提供下列的命令列工具來檢視或操作組建輸出：

[C/C++ 建置錯誤](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
導入了組建錯誤區段的資料表中的內容。

## <a name="related-sections"></a>相關章節

[C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
討論的前置處理器巨集、 運算子和指示詞的轉譯準備編譯器的原始程式檔。

[了解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)<br/>
討論自訂建置流程。

[建置 C/c + + 程式](../../build/building-c-cpp-programs.md)<br/>
提供描述如何從命令列或 Visual Studio 整合式開發環境建置程式等主題的連結。

[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
描述在開發環境中或在命令列上，設定編譯器選項。

[編譯器選項](../../build/reference/compiler-options.md)<br/>
提供討論使用編譯器選項的主題連結。

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
描述內部或外部的整合式的開發環境設定連結器選項。

[連結器選項](../../build/reference/linker-options.md)<br/>
提供討論使用連結器選項的主題連結。

[BSCMAKE 參考](../../build/reference/bscmake-reference.md)<br/>
描述 Microsoft 瀏覽資訊維護公用程式 (BSCMAKE。EXE)，哪些組建會瀏覽資訊檔 (.bsc) 從.sbr 檔案在編譯期間建立。

[LIB 參考](../../build/reference/lib-reference.md)<br/>
描述 Microsoft 的程式庫管理員 (LIB.exe)，它會建立並管理通用物件檔案格式 (COFF) 物件檔的程式庫。

[EDITBIN 參考](../../build/reference/editbin-reference.md)<br/>
描述 Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE) 這麼做會修改通用物件檔案格式 (COFF) 二進位檔。

[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)<br/>
描述 Microsoft COFF 二進位檔傾印工具 (DUMPBIN。EXE)，其中顯示通用物件檔案格式 (COFF) 的二進位檔案的相關資訊。

[NMAKE 參考](../../build/nmake-reference.md)<br/>
描述 Microsoft Program Maintenance Utility (NMAKE。這是一種工具，建置專案的 EXE)，根據描述檔案中包含的命令。