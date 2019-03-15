---
title: BSCMAKE 選項
ms.date: 11/04/2016
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
ms.openlocfilehash: bf4c3648079dff16481dbdd56b9a70093fd22d8d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812053"
---
# <a name="bscmake-options"></a>BSCMAKE 選項

本節說明可用來控制 BSCMAKE 選項。 數個選項可控制瀏覽資訊檔的內容所排除或包含特定資訊。 排除選項可讓執行速度更快的 BSCMAKE，可能會導致較小的.bsc 檔案。 選項名稱會區分大小寫 (除了 **/help**並 **/NOLOGO**)。

只有 **/NOLOGO**並 **/o**都是從 Visual Studio 開發環境中。  請參閱[在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)如需存取 專案屬性頁。

**/Ei (** *filename*...**)**<br/>
瀏覽資訊檔中排除指定的 include 檔案的內容。 若要指定多個檔案，以空格分隔的名稱，並以括弧括住的清單。 括號不需要，如果您只指定一個*filename*。 使用 **/Ei**連同 **/Es**選項來排除檔案未排除 **/Es**。

**/El**<br/>
不包括本機符號。 預設值是包含本機符號。 如需有關本機符號的詳細資訊，請參閱[建立.sbr 檔](creating-an-dot-sbr-file.md)。

**/Em**<br/>
排除的巨集主體中的符號。 使用 **/e m**瀏覽資訊檔中包含的巨集名稱。 預設值是包含巨集名稱和巨集展開的結果。

**/Er (** *符號*...**)**<br/>
瀏覽資訊檔中排除指定的符號。 若要指定多個符號名稱，以空格分隔的名稱，並以括弧括住的清單。 括號不需要，如果您只指定一個*符號*。

**/Es**<br/>
從瀏覽資訊檔中排除指定的絕對路徑，或在 INCLUDE 環境變數中指定的絕對路徑中找到每個 include 檔案。 (這些通常是系統 include 檔案，其中包含許多您可能不需要在您瀏覽資訊檔的資訊。)此選項不會排除沒有路徑或相對路徑或檔案中包含的相對路徑中找到指定的檔案。 您可以使用 **/Ei**連同選項 **/Es**排除的檔案 **/Es**不會排除。 如果您想要排除部分一個檔案， **/Es**排除，使用 **/Ei**而非 **/Es**並列出您想要排除的檔案。

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
可讓您傳送給 Microsoft 的資訊，關於 bscmake.exe 中的內部錯誤。

如需詳細資訊 **/errorreport**，請參閱[/errorReport （回報編譯器內部錯誤）](errorreport-report-internal-compiler-errors.md)。

**/HELP**<br/>
顯示 BSCMAKE 命令列語法摘要。

**/Iu**<br/>
包含未參考的符號。 根據預設，BSCMAKE 就不會記錄已定義但未參考任何符號。 如果封裝的.sbr 檔，此選項會有任何作用，該輸入檔案，因為編譯器可能移除未參考的符號。

**/n**<br/>
會強制執行非累加建置。 使用 **/n**強制.bsc 檔案是否存在的瀏覽資訊檔的完整建置，並防止.sbr 檔被截斷。 請參閱[BSCMAKE 如何建置.bsc 檔](how-bscmake-builds-a-dot-bsc-file.md)。

**/NOLOGO**<br/>
隱藏 BSCMAKE 著作權訊息。

**/o** *filename*<br/>
指定瀏覽資訊檔的名稱。 根據預設，BSCMAKE 會提供瀏覽資訊檔的第一個的.sbr 檔案以及.bsc 延伸模組的基底名稱。

**/S (** *filename*...**)**<br/>
會告知 BSCMAKE 來處理指定的 include 檔時發現的第一次並否則排除它。 使用此選項，以節省處理時間，當包含數個原始程式檔中的檔案 （如標頭，或.h、 檔案.c 或.cpp 原始程式檔），但並不會變更每次前置處理器指示詞。 您也可以使用此選項，如果檔案在不重要，您要建立瀏覽資訊檔的方式變更。 若要指定多個檔案，以空格分隔的名稱，並以括弧括住的清單。 括號不需要，如果您只指定一個*filename*。 如果您想要排除的檔案，每當它未包含，請使用 **/Ei**或是 **/Es**選項。

**/v**<br/>
提供詳細資訊輸出，其中包含的每個正在處理的.sbr 檔案名稱和執行完整 BSCMAKE 的相關資訊。

**/?**<br/>
顯示 BSCMAKE 命令列語法的簡短摘要。

下列命令列會告訴您從三個.sbr 檔案執行完整建置 MAIN.bsc BSCMAKE。 它也會告訴 BSCMAKE 來排除重複的執行個體的 TOOLBOX.h:

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>另請參閱

[BSCMAKE 參考](bscmake-reference.md)
