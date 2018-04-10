---
title: BSCMAKE 選項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- C++
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46c258a5591615bb277823ccc5261fade3c5e2af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-options"></a>BSCMAKE 選項
本節描述可用來控制 BSCMAKE 選項。 數個選項控制排除或包含特定資訊，以瀏覽資訊檔的內容。 排除選項可以允許 BSCMAKE 執行得比較快，而且可能造成較小的.bsc 檔中。 選項名稱會區分大小寫 (除了**/help**和**/NOLOGO**)。  
  
 只有**/NOLOGO**和**/o**都是從 Visual Studio 開發環境中。  請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)如需存取 專案屬性頁。  
  
 /Ei ( `filename`...)  
 瀏覽資訊檔中排除指定的包含檔案的內容。 若要指定多個檔案，以空格分隔名稱和括號括住的清單。 括號並非必要，如果您只指定一個`filename`。 使用**/Ei**連同**/Es**選項來排除檔案未排除**/Es**。  
  
 /El  
 排除本機符號。 預設值是包含本機符號。 如需本機符號的詳細資訊，請參閱[建立.sbr 檔](../../build/reference/creating-an-dot-sbr-file.md)。  
  
 / E m  
 排除的巨集主體中的符號。 使用**/e m**要在瀏覽資訊檔中包含的巨集名稱。 預設值是包含巨集名稱和巨集展開的結果。  
  
 /Er ( `symbol`...)  
 瀏覽資訊檔中排除指定的符號。 若要指定多個符號名稱，以空格分隔名稱和括號括住的清單。 括號並非必要，如果您只指定一個`symbol`。  
  
 /Es  
 指定絕對路徑，或在 INCLUDE 環境變數中指定的絕對路徑中找到的每個 include 檔案排除瀏覽資訊檔。 (這些通常是系統 include 檔，其中包含許多您可能不需要在您瀏覽資訊檔中的資訊。)這個選項不會排除沒有路徑或相對路徑或檔案中包含的相對路徑中找到指定的檔案。 您可以使用**/Ei**選項連同**/Es**排除的檔案**/Es**未排除。 如果您想要排除部分一個檔案， **/Es**排除，使用**/Ei**而不是**/Es**並列出您想要排除的檔案。  
  
 /errorreport: [無 &#124; 提示字元 &#124; 佇列 &#124; 傳送]  
 可讓您將資訊傳送給 Microsoft，關於 bscmake.exe 中的內部錯誤。  
  
 如需有關**/errorreport**，請參閱[/errorReport （回報編譯器內部錯誤）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 /HELP  
 顯示 BSCMAKE 命令列語法的摘要。  
  
 /Iu  
 包含未參考的符號。 根據預設，BSCMAKE 就不會記錄已定義但未參考任何符號。 如果壓縮的.sbr 檔案，此選項會有任何作用，輸入檔案，因為編譯器移除未參考的符號。  
  
 /n  
 會強制執行非累加建置。 使用 **/n** 強制.bsc 檔案是否存在瀏覽資訊檔的完整建置，並防止.sbr 檔被截斷。 請參閱[BSCMAKE 如何建置.bsc 檔](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md)。  
  
 /NOLOGO  
 隱藏 BSCMAKE 著作權訊息。  
  
 /o`filename`  
 指定瀏覽資訊檔的名稱。 根據預設，BSCMAKE 會提供瀏覽資訊檔的第一個的.sbr 檔案以及.bsc 延伸模組的基底名稱。  
  
 /S ( `filename`...)  
 會告知 BSCMAKE 處理指定的包含檔案時發現的第一次，則排除。 使用此選項，以節省處理時間時 （例如標頭，或.h、 檔案.c 或.cpp 的原始程式檔） 檔案包含數個原始程式檔中，但並不會變更每次前置處理器指示詞。 您也可以使用此選項，如果檔案已變更的方式對於您要建立瀏覽資訊檔不重要。 若要指定多個檔案，以空格分隔名稱和括號括住的清單。 括號並非必要，如果您只指定一個`filename`。 如果您想要每次它也會排除的檔案，請使用**/Ei**或**/Es**選項。  
  
 /v  
 提供詳細資訊輸出，其中包括正在處理每個.sbr 檔案的名稱和執行完整 BSCMAKE 的相關資訊。  
  
 /?  
 顯示 BSCMAKE 命令列語法的簡短摘要。  
  
 下列的命令列會告訴您要從三個.sbr 檔案執行完整建置 MAIN.bsc BSCMAKE。 它也會告訴以排除重複的執行個體 TOOLBOX.h BSCMAKE:  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## <a name="see-also"></a>請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)