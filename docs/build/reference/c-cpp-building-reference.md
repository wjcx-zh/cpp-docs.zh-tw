---
title: C /C++建置參考-Visual Studio
description: 參考的內容適用於 C /C++專案系統，並建置在 Visual Studio 中的工具。
ms.date: 12/10/2018
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 4c3f7aa598a9c43af04c148ed0d4b3f555566ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294755"
---
# <a name="cc-building-reference"></a>C/C++ 建置參考

視覺化C++提供兩種方式建置 C /C++程式。 最簡單 （且最常見） 的方式為： [Visual Studio IDE 中建置](../creating-and-managing-visual-cpp-projects.md)。 其他的方式為[命令提示字元使用命令列工具來建立](../building-on-the-command-line.md)。 在任一情況下，您可以建立和編輯使用 Visual Studio 或您選擇的協力廠商編輯器的原始程式檔。

## <a name="in-this-section"></a>本節內容

[C ++ 專案的 MSBuild 參考](msbuild-visual-cpp-overview.md)

[MSVC 編譯器參考](compiling-a-c-cpp-program.md)<br/>
描述 MSVC 編譯器，這會建立包含機器碼，連結器指示詞、 區段、 外部參考，以及函式/資料名稱的物件檔案。

[MSVC 連結器參考](linking.md)<br/>
說明連結器，其結合了來自編譯器所建立的物件檔案和靜態連結程式庫程式碼，會解析名稱的參考，並建立可執行檔。

[編譯器和連結器中的 Unicode 支援](unicode-support-in-the-compiler-and-linker.md)

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
其他的命令列工具C++。

[C/C++ 建置錯誤](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
導入了組建錯誤區段的資料表中的內容。

## <a name="related-sections"></a>相關章節

[C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
討論的前置處理器巨集、 運算子和指示詞的轉譯準備編譯器的原始程式檔。

[了解自訂建置步驟和建置事件](../understanding-custom-build-steps-and-build-events.md)<br/>
討論自訂建置流程。

[建置 C /C++計劃](../projects-and-build-systems-cpp.md)<br/>
提供描述如何從命令列或 Visual Studio 整合式開發環境建置程式等主題的連結。

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
描述在開發環境中或在命令列上，設定編譯器選項。

[MSVC 編譯器選項](compiler-options.md)<br/>
提供討論使用編譯器選項的主題連結。

[MSVC 連結器參考](linking.md)<br/>
描述內部或外部的整合式的開發環境設定連結器選項。

[MSVC 連結器選項](linker-options.md)<br/>
提供討論使用連結器選項的主題連結。

[BSCMAKE 參考](bscmake-reference.md)<br/>
描述 Microsoft 瀏覽資訊維護公用程式 (BSCMAKE。EXE)，哪些組建會瀏覽資訊檔 (.bsc) 從.sbr 檔案在編譯期間建立。

[LIB 參考](lib-reference.md)<br/>
描述 Microsoft 的程式庫管理員 (LIB.exe)，它會建立並管理通用物件檔案格式 (COFF) 物件檔的程式庫。

[EDITBIN 參考](editbin-reference.md)<br/>
描述 Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE) 這麼做會修改通用物件檔案格式 (COFF) 二進位檔。

[DUMPBIN 參考](dumpbin-reference.md)<br/>
描述 Microsoft COFF 二進位檔傾印工具 (DUMPBIN。EXE)，其中顯示通用物件檔案格式 (COFF) 的二進位檔案的相關資訊。

[NMAKE 參考](nmake-reference.md)<br/>
描述 Microsoft Program Maintenance Utility (NMAKE。這是一種工具，建置專案的 EXE)，根據描述檔案中包含的命令。
