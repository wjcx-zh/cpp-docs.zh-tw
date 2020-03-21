---
title: MIDL 編譯器屬性頁
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 260936d01a611f061b0b4fa9a5c087ff38cc66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076136"
---
# <a name="midl-property-pages"></a>MIDL 屬性頁

MIDL 屬性頁在上是以專案屬性的形式提供。使用 COM 之C++專案中的 IDL 檔案。 使用它們來設定[MIDL 編譯器](/windows/win32/midl/using-the-midl-compiler-2)。 如需如何以程式設計方式存取 C++ 專案的 MIDL 選項的資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 物件。 另請參閱[一般 MIDL 命令列語法](/windows/win32/midl/general-midl-command-line-syntax)。

## <a name="general-property-page"></a>一般屬性頁

### <a name="preprocessor-definitions"></a>前置處理器定義

指定一或多個定義，包括 MIDL 宏（[/d](/windows/win32/midl/-d)）\[宏\]）。

### <a name="additional-include-directories"></a>其他 Include 目錄

指定一或多個要新增至 include 路徑的目錄（[/i](/windows/win32/midl/-i)\[路徑\]）。

### <a name="additional-metadata-directories"></a>其他中繼資料目錄

指定包含 Windows. Foundation WinMD 檔案（[/metadata_dir](/windows/win32/midl/-metadata-dir) \[路徑\]）的目錄。

### <a name="enable-windows-runtime"></a>啟用 Windows 執行階段

啟用 Windows 執行階段的語義來建立 Windows 中繼資料檔（[/winrt](/windows/win32/midl/-winrt)）。

### <a name="ignore-standard-include-path"></a>忽略標準 Include 路徑

忽略目前的和 INCLUDE 目錄（[/no_def_idir](/windows/win32/midl/-no-def-idir)）。

### <a name="mktyplib-compatible"></a>Mktyplib.exe 相容

強制與 mktyplib.exe 2.03 版（[/mktyplib203](/windows/win32/midl/-mktyplib203)）相容。

### <a name="warning-level"></a>警告等級

選取 MIDL 程式碼錯誤（[/w](/windows/win32/midl/-w)）的嚴謹度。

**Choices**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>將警告視為錯誤

讓 MIDL 將所有警告視為錯誤（[/wx](/windows/win32/midl/-wx)）。

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

隱藏啟動橫幅和資訊訊息（[/nologo](/windows/win32/midl/-nologo)）的顯示。

### <a name="c-compiler-char-type"></a>C 編譯器 Char 類型

指定將用來編譯所產生程式碼的 C 編譯器的預設字元類型。 （[/char](/windows/win32/midl/-char)已簽署 | 未簽署 | ascii7）。

**Choices**

- **已簽署**簽署
- 不帶**正負**號
- **Ascii** -ascii

### <a name="target-environment"></a>目標環境

指定要設為目標的環境（[/env](/windows/win32/midl/-env) arm32 | win32 | ia64 | x64）。

**Choices**

- **未設定**-Win32
- **Microsoft Windows 32 位**-Win32
- **Itanium 上的 Microsoft Windows 64 位**-IA64
- **Microsoft WINDOWS arm** -arm
- **Microsoft WINDOWS ARM64** -ARM64
- **X64 上的 Microsoft Windows 64 位**-x64

### <a name="generate-stubless-proxies"></a>產生 Stubless proxy

使用物件介面（[/Oicf](/windows/win32/midl/-oi)、 [/Oif](/windows/win32/midl/-oi) ）的延伸模組和 stubless proxy，產生完全解讀的存根。

### <a name="suppress-compiler-warnings"></a>隱藏編譯器警告

隱藏編譯器警告訊息（[/no_warn](/windows/win32/midl/-no-warn)）。

### <a name="application-configuration-mode"></a>應用程式設定模式

允許在 IDL 檔案中選取的 ACF 屬性（[/app_config](/windows/win32/midl/-app-config)）。

### <a name="locale-id"></a>地區識別碼

指定輸入檔的 LCID、檔案名和目錄路徑（[/Lcid](/windows/win32/midl/-lcid) DECIMAL）。

### <a name="multi-processor-compilation"></a>多處理器編譯

同時執行多個實例。

## <a name="output-property-page"></a>輸出屬性頁

### <a name="output-directory"></a>輸出目錄

指定輸出目錄（[/out](/windows/win32/midl/-out) [目錄]）。

### <a name="metadata-file"></a>中繼資料檔案

指定所產生中繼資料檔案的名稱（[/winmd](/windows/win32/midl/-winmd) filename）。

### <a name="header-file"></a>標頭檔

指定所產生之標頭檔的名稱（[/h](/windows/win32/midl/-h) filename）。

### <a name="dlldata-file"></a>Dlldata.c 檔案

指定 DLLDATA.C 檔的名稱（[/dlldata](/windows/win32/midl/-dlldata) filename）。

### <a name="iid-file"></a>IID 檔案

指定介面識別碼檔的名稱（[/iid](/windows/win32/midl/-iid) filename）。

### <a name="proxy-file"></a>Proxy 檔案

指定 proxy 檔案的名稱（[/proxy](/windows/win32/midl/-proxy) filename）。

### <a name="generate-type-library"></a>產生類型程式庫

指定不產生類型程式庫（[/notlb] 代表否）。

### <a name="type-library"></a>類型程式庫

指定類型程式庫檔案的名稱（[/tlb](/windows/win32/midl/-tlb) filename）。

### <a name="generate-client-stub-files"></a>產生用戶端 Stub 檔案

僅產生用戶端 stub 檔案（[/client](/windows/win32/midl/-client) [stub | none]）。

**Choices**

- **存根**-stub
- **無**-無

### <a name="generate-server-stub-files"></a>產生伺服器 Stub 檔案

僅產生伺服器 stub 檔案（[/server](/windows/win32/midl/-server) [stub | none]）。

**Choices**

- **存根**-stub
- **無**-無

### <a name="client-stub-file"></a>用戶端 Stub 檔案

指定用戶端 stub 檔案（[/cstub](/windows/win32/midl/-cstub) [檔案]）。

### <a name="server-stub-file"></a>伺服器 Stub 檔案

指定伺服器 stub 檔（[/sstub](/windows/win32/midl/-sstub) [檔案]）。

### <a name="type-library-format"></a>型別程式庫格式

指定類型程式庫檔案格式（[/oldtlb |/newtlb]）。

**Choices**

- **NewFormat** -新格式
- **OldFormat** -舊格式

## <a name="advanced-property-page"></a>Advanced 屬性頁

### <a name="c-preprocess-options"></a>C 前置處理選項

指定要傳遞至 C 編譯器預處理器（[/cpp_opt](/windows/win32/midl/-cpp-opt)參數）的參數。

### <a name="undefine-preprocessor-definitions"></a>取消前置處理器的定義

指定一或多個取消加入，包括 MIDL 宏（[/u](/windows/win32/midl/-U) [宏]）。

### <a name="enable-error-checking"></a>啟用錯誤檢查

選取錯誤檢查選項（[/error 全部 | 無]）。

**Choices**

- **EnableCustom** -全部
- **全部**-全部
- **無**-無

### <a name="check-allocations"></a>檢查配置

檢查是否有記憶體不足的錯誤（[/error](/windows/win32/midl/-error)配置）。

### <a name="check-bounds"></a>檢查界限

檢查大小與傳輸長度規格（[/error](/windows/win32/midl/-error) bounds_check）。

### <a name="check-enum-range"></a>檢查列舉範圍

檢查列舉值是否在允許的範圍內（[/error](/windows/win32/midl/-error)列舉）。

### <a name="check-reference-pointers"></a>檢查參考指標

請檢查 ref 指標是否為非 null （[/error](/windows/win32/midl/-error) ref）。

### <a name="check-stub-data"></a>檢查存根資料

發出伺服器端存根資料有效性的額外檢查（[/error](/windows/win32/midl/-error) stub_data）。

### <a name="prepend-with-abi-namespace"></a>前面加上 ' ABI ' 命名空間

在所有類型前面加上 ' ABI ' 命名空間。  （[/ns_prefix](/windows/win32/midl/-ns-prefix)）。

### <a name="validate-parameters"></a>驗證參數

產生其他資訊來驗證參數（[/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)）。

### <a name="struct-member-alignment"></a>結構成員對齊

指定目標系統中結構的封裝層級（/ZpN）。

**Choices**

- **未設定**-未設定
- **1 個位元組**-Zp1
- **2 個位元組**-Zp2
- **4 個位元組**-Zp4
- **8 個位元組**-Zp8

### <a name="redirect-output"></a>重新導向輸出

將畫面的輸出重新導向至檔案（[/o](/windows/win32/midl/-o)檔案）。

### <a name="minimum-target-system"></a>最小目標系統

設定最小目標系統（[/Target](/windows/win32/midl/-target) STRING）。
