---
title: BSCMAKE 選項
description: Microsoft BSCMAKE 公用程式命令列選項的參考。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257789"
---
# <a name="bscmake-options"></a>BSCMAKE 選項

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 由於 Visual Studio 2008，流覽和符號資訊會自動儲存在方案資料夾的 SQL Server *`.sdf`* 檔案中。

本節說明可用來控制 BSCMAKE 的選項。 有數個選項會藉由排除或包含特定資訊來控制流覽資訊檔案的內容。 排除選項可以讓 BSCMAKE 執行得更快，而且可能會產生較小的 *`.bsc`* 檔案。 選項名稱會區分大小寫（ **/help**和 **/nologo**除外）。

只有 **/nologo**和 **/o**可從 Visual Studio 開發環境中取得。  如需存取專案屬性頁的資訊，請參閱[在 Visual Studio 中設定C++編譯器和組建屬性](../working-with-project-properties.md)。

**/Ei （** _filename_.。**）** \
從流覽資訊檔案中排除指定之 include 檔的內容。 若要指定多個檔案，請以空格分隔名稱，並以括弧括住清單。 如果您只指定一個*檔案名*，則不需要括弧。 使用 **/Ei**搭配 **/Es**選項，以排除 **/Es**未排除的檔案。

**/El**\
排除本機符號。 預設為包含本機符號。 如需本機符號的詳細資訊，請參閱[建立 .sbr](creating-an-dot-sbr-file.md)檔案。

**/Em**\
在宏主體中排除符號。 請使用 **/Em** ，只在流覽資訊檔案中包含宏的名稱。 預設為同時包含宏名稱和宏展開的結果。

**/Er （** _符號_.。**）** \
從流覽資訊檔案中排除指定的符號。 若要指定多個符號名稱，請以空格分隔名稱，並以括弧括住清單。 如果您只指定一個*符號*，則不需要括弧。

**/Es**\
排除以絕對路徑指定的每個 include 檔案，或在 INCLUDE 環境變數中指定的絕對路徑中找到的檔案。 （這些檔案通常是系統 include 檔案，其中包含您在流覽資訊檔案中可能不需要的許多資訊）。此選項不會排除指定不含路徑的檔案或具有相對路徑的檔案，或是在包含的相對路徑中找到的檔案。 您可以使用 **/Ei**選項搭配 **/Es** ，以排除 **/Es**不會排除的檔案。 如果您只想要排除部分檔案，請使用 **/Ei**而不是 **/Es**，並列出您要排除的檔案。

**/errorreport：** [**無** &#124; **提示** &#124; **佇列** &#124; **傳送**] \
這個選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

**/Help**\
顯示 BSCMAKE 命令列語法的摘要。

**/Iu**\
包含未參考的符號。 根據預設，BSCMAKE 不會記錄已定義但未參考的任何符號。 如果已封裝 *`.sbr`* 檔案，這個選項就不會影響該輸入檔，因為編譯器已移除未參考的符號。

**/n**\
強制執行非累加組建。 使用 **/n**來強制執行流覽資訊檔案的完整組建，不論 *`.bsc`* 檔案是否存在，以及防止 *`.sbr`* 的檔案遭到截斷。 瞭解[BSCMAKE 如何建立 .bsc](how-bscmake-builds-a-dot-bsc-file.md)檔案。

**/Nologo**\
抑制 BSCMAKE 著作權訊息。

**/o** *filename*\
指定流覽資訊檔的名稱。 根據預設，BSCMAKE 會為流覽資訊檔案提供第一個 *`.sbr`* 檔案的基底名稱和 *`.bsc`* 延伸模組。

**/S （** _filename_.。**）** \
告訴 BSCMAKE 在第一次遇到指定的 include 檔案時處理該檔案，否則會將其排除。 使用此選項可儲存檔案（例如， *`.c`* 或 *`.cpp`* 原始程式檔的標頭或 *`.h`* 檔案）包含在多個原始程式檔中的處理時間，但每次都由前置處理指示詞變更。 如果檔案的變更方式與您要建立的流覽資訊檔案不重要，請使用此選項。 若要指定多個檔案，請以空格分隔名稱，並以括弧括住清單。 如果您只指定一個*檔案名*，則不需要括弧。 如果您想要在每次包含檔案時排除該檔案，請使用 **/Ei**或 **/Es**選項。

**/v**\
提供詳細資訊輸出，其中包括正在處理的每個 *`.sbr`* 檔案的名稱，以及完整 BSCMAKE 執行的相關資訊。

**/?** \
顯示 BSCMAKE 命令列語法的簡短摘要。

下列命令列會告訴 BSCMAKE 從三個 *`.sbr`* 檔案執行主要 .bsc 的完整組建。 它也會告訴 BSCMAKE 排除重複的 [工具箱] 實例。 h：

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>另請參閱

[BSCMAKE 參考](bscmake-reference.md)
