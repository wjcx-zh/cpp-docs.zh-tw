---
title: "C/C++ 屬性 (Linux C++) | Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.AdditionalWarning
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.UnrollLoops
- VC.Project.VCClangCompilerTool.LinkTimeOptimization
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.NoCommonBlocks
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.ThreadSafeStatics
- VC.Project.VCClangCompilerTool.RelaxIEEE
- VC.Project.VCClangCompilerTool.HideInlineMethods
- VC.Project.VCClangCompilerTool.SymbolsHiddenByDefault
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- vc.project.AdditionalOptionsPage
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 096775841841574571b7ef731db52f3bbda6485f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cc-properties-linux-c"></a>C/C++ 屬性 (Linux C++)

## <a name="general"></a>一般
屬性 | 描述 | 選擇
--- | ---| ---
其他 Include 目錄 | 指定一或多個要新增至 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。 (-I[路徑])。
偵錯資訊格式 | 指定編譯器所產生的偵錯資訊類型。 | **無** - 因為不產生任何偵錯資訊，所以編譯速度會較快。<br>**最少偵錯資訊** - 產生最少的偵錯資訊。<br>**完整偵錯資訊 (DWARF2)** - 產生 DWARF2 偵錯資訊。<br>
物件檔案名稱 | 指定要覆寫預設物件檔案名稱的名稱；可以是檔案或目錄名稱。 (-o [名稱])。
警告層級 | 選取您希望編譯器針對程式碼錯誤所產生的嚴謹度等級。  其他旗標會直接新增到 [其他選項]。 (/w, /Weverything)。 | **關閉所有警告** - 停用所有編譯器警告。<br>**啟用所有警告** - 啟用所有警告，包括預設為停用的警告。<br>
將警告視為錯誤 | 將所有編譯器警告視為錯誤。 若是新專案，建議在所有編譯中使用 /Werror；解決所有警告可確保難以找到的程式碼缺失數最少。
C 其他警告 | 定義一組其他警告訊息。
C + + 其他警告 | 定義一組其他警告訊息。
啟用詳細資訊模式 | 啟用詳細資訊模式時，這項工具會列印出用於診斷組建的詳細資訊。
C 編譯器 | 指定在 C 來源檔案編譯期間要叫用的程式，或遠端系統上 C 編譯器的路徑。
C++ 編譯器 | 指定在 C++ 來源檔案編譯期間要叫用的程式，或遠端系統上 C++ 編譯器的路徑。
編譯逾時 | 遠端編譯逾時 (毫秒)。
複製物件檔 | 指定是否要從遠端系統將經過編譯的物件檔，複製到本機電腦上。

## <a name="optimization"></a>最佳化
屬性 | 描述 | 選擇
--- | ---| ---
最佳化 | 指定應用程式的最佳化層級。 | **自訂** - 自訂最佳化。<br>**停用** - 停用最佳化。<br>**最小化程式碼** - 大小最佳化。<br>**最快速度** - 速度最佳化。<br>**完整最佳化** - 最費時的最佳化。<br>
嚴格的別名 | 採用最嚴格的別名規則。  一律不會將一種類型的物件，視為位於與不同類型物件位於相同的位址上。
展開迴圈 | 展開迴圈，以程式碼大小較大來換取執行分支數較少的方式，加快應用程式的速度。
連結時間最佳化 | 啟用程序間最佳化，方式是允許最佳化工具跨您應用程式中的物件檔進行搜尋。
省略框架指標 | 在呼叫堆疊上隱藏框架指標的建立。
禁止通用區塊 | 在物件檔的資料區段配置平均的未初始化全域變數，而非將其產生為通用區塊

## <a name="preprocessor"></a>前置處理器
屬性 | 描述 | 選擇
--- | ---| ---
前置處理器定義 | 定義來源檔案的前置處理符號。 (-D)
取消前置處理器的定義 | 指定取消一或多個前置處理器的定義。  (-U [巨集])
取消所有前置處理器的定義 | 取消所有先前定義的前置處理器值。  (-undef)
顯示 Include | 產生 Include 檔清單以及編譯器輸出。  (-H)

## <a name="code-generation"></a>程式碼產生
屬性 | 描述 | 選擇
--- | ---| ---
位置獨立程式碼 | 產生位置獨立程式碼 (PIC) 以用於共用程式庫。
靜態為安全執行緒 | 為區域靜態的執行緒安全初始化發出額外的程式碼，以使用在 C++ ABI 中指定的常式。 | **否** - 停用執行緒安全靜態。<br>**是** - 啟用執行緒安全靜態。<br>
浮點數最佳化 | 放寬 IEEE-754 規範可啟用浮點數最佳化。
內嵌方法隱藏 | 啟用時，內嵌方法的非內嵌複本會宣告為 'private extern'。
預設會隱藏符號 | 所有符號都會宣告為 'private extern'，除非其已明確標示為將使用 '__attribute' 巨集進行匯出。
啟用 C++ 例外狀況 | 指定編譯器所使用的例外狀況處理模型。 | **否** - 停用例外狀況處理。<br>**是** - 啟用例外狀況處理。<br>

## <a name="language"></a>語言
屬性 | 描述 | 選擇
--- | ---| ---
啟用執行階段類型資訊 | 新增在執行階段用於檢查 C++ 物件類型的程式碼 (執行階段類型資訊)。     (frtti、fno-rtti)
C 語言標準 | 決定 C 語言標準。 | **Default**<br>**C89** - C89 語言標準。<br>**C99** - C99 語言標準。<br>**C11** - C11 語言標準。<br>**C99 (GNU 方言)** - C99 (GNU 方言) 語言標準。<br>**C11 (GNU 方言)** - C11 (GNU 方言) 語言標準。<br>
C + + 語言標準 | 決定 C++ 語言標準。 | **Default**<br>**C++03** - C++03 語言標準。<br>**C++11** - C++11 語言標準。<br>**C++14** - C++14 語言標準。<br>**C++03 (GNU 方言)** - C++03 (GNU 方言) 語言標準。<br>**C++11 (GNU 方言)** - C++11 (GNU 方言) 語言標準。<br>**C++14 (GNU 方言)** - C++14 (GNU 方言) 語言標準。<br>

## <a name="advanced"></a>進階
屬性 | 描述 | 選擇
--- | ---| ---
編譯為 | 選取 .c 和 .cpp 檔的編譯語言選項。  'Default' 會根據 .c 或 .cpp 副檔名進行偵測。 (-x c、-x c++) | **預設** - 預設值。<br>**編譯成 C 程式碼** - 編譯成 C 程式碼。<br>**編譯成 C++ 程式碼** - 編譯成 C++ 程式碼。<br>
強制的 Include 檔案 | 一或多個強制的 Include 檔案。 (-include [名稱])

## <a name="additional-options"></a>其他選項 