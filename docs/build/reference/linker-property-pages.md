---
title: 連結器屬性頁
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336592"
---
# <a name="linker-property-pages"></a>連結器屬性頁

以下屬性位於**專案** > **屬性** > **配置屬性** > **連結器**下。 有關連結器的詳細資訊,請參閱 CL[呼叫連結器](cl-invokes-the-linker.md)與[連結器選項](linker-options.md)。

## <a name="general-property-page"></a>一般屬性頁

### <a name="output-file"></a>輸出檔案

[/OUT](out-output-file-name.md)選項將覆蓋連結器創建的程式的預設名稱和位置。

### <a name="show-progress"></a>顯示進度

列印連結進度訊息

**Choices**

- **未設置**- 無詳細性。
- **顯示所有進度訊息**- 顯示所有進度訊息。
- **對於搜尋的庫**- 顯示顯示顯示僅搜尋的庫的進度消息。
- **關於最佳化連結期間的 COMDAT 摺疊**- 在最佳化連結期間顯示有關 COMDAT 摺疊的資訊。
- **關於最佳化連結期間刪除的資料**- 顯示有關優化連結期間刪除的函數和資料的資訊。
- **關於與 SEH 不相容的模組**- 顯示與安全異常處理不相容的模組的資訊。
- **關於與託管代碼相關的連結器活動**- 顯示有關連結器活動的資訊,這些活動與託管代碼相關。

### <a name="version"></a>版本

[/VERSION](version-version-information.md)選項告訴連結器將版本號放在 .exe 或 .dll 檔的標頭中。 使用 DUMPBIN/HEADERS 查看"可選標題"的圖像版本欄位以查看 **/VERSION**的效果。

### <a name="enable-incremental-linking"></a>啟用累加連結

啟用增量連結。 [(/增量](incremental-link-incrementally.md),/增量:否)

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

[/NOLOGO](nologo-suppress-startup-banner-linker.md)選項可防止顯示版權消息和版本號。

### <a name="ignore-import-library"></a>忽略匯入程式庫

這個屬性會告知連結器不要將這個組建所產生的任何 .lib 輸出連結到任何相依專案。 它允許專案系統處理生成時不生成 .lib 檔的 .dll 檔。 如果專案相依於另一個會產生 DLL 的專案，則專案系統會自動連結該個子專案所產生的 .lib 檔。 在生成 COM DLL 或僅資源 DLL 的專案中,此屬性可能沒有必要,因為這些 DLL 沒有任何有意義的匯出。 如果 DLL 沒有匯出,則連結器不會生成 .lib 檔。 如果不存在匯出 .lib 檔,並且專案系統告訴連結器與缺少的 DLL 連結,則連結將失敗。 請使用 [忽略匯入程式庫]**** 屬性來解決此問題。 當設定為 **「是**」時,專案系統將忽略 .lib 檔的存在或不存在,並導致依賴於此專案的任何專案不連結到不存在的 .lib 檔。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>登錄輸出

對組建輸出執行 `regsvr32.exe /s $(TargetPath)`，這只有在 .dll 專案上才有效。 對於 .exe 專案，則會忽略這個屬性。 若要註冊 .exe 輸出，請在組態上設定建置後事件，以執行已註冊之 .exe 檔一律需要的自訂登錄。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>個別使用者重新導向

Visual Studio 中的註冊傳統上都在 HKEY_CLASSES_ROOT (HKCR) 進行。 使用 Windows Vista 和更新版本的作業系統，若要存取 HKCR 您必須以提升權限模式執行 Visual Studio。 開發人員並不總是希望在提升模式下運行,但仍必須使用註冊。 每個使用者重定向允許您註冊,而無需在提升模式下運行。

個別使用者重新導向會強制將 HKCR 的任何寫入重新導向至 HKEY\_CURRENT\_USER (HKCU)。 如果關閉每個使用者重新導向，它可能會在程式嘗試寫入 HKCR 時導致[專案建置錯誤 PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="additional-library-directories"></a>其他程式庫目錄

允許使用者覆寫環境程式庫路徑。 [(/LIBPATH](libpath-additional-libpath.md):資料夾)

### <a name="link-library-dependencies"></a>連結程式庫相依性

指定是否要連結由相依專案所產生的 .lib 檔。 通常,您希望在 .lib 檔中連結,但某些 DLL 可能不是這樣。

您也可以提供檔案名稱和相對路徑以指定 .obj 檔案，例如 "..\\..\MyLibProject\MyObjFile.obj"。 如果 .obj 檔案的原始程式碼#includes預編譯的標頭(例如 pch.h),則 pch.obj 檔與 MyObjFile.obj 位於同一檔夾中。您還必須添加 pch.obj 作為附加依賴項。

### <a name="use-library-dependency-inputs"></a>使用程式庫相依性輸入

指定在項目依賴項的庫輸出中連結時,是否將輸入用於圖書管理員工具,而不是庫檔本身。 在大型專案中，當相依專案產生 .lib 檔時，會停用累加連結。 如果有許多相依專案產生 .lib 檔，建置應用程式可能會花很長的時間。 當此屬性設置為 **「是**」時,專案系統將連結在由從屬專案生成的.obj 檔中的.obj 檔中,從而啟用增量連結。

有關如何存**取 一般**連結器屬性頁的資訊,請參閱在 Visual [Studio 中設定 C++編譯器和產生屬性](../working-with-project-properties.md)。

### <a name="link-status"></a>連結狀態

指定連結器是否應顯示進度指示器,顯示連結已完成的百分比。 預設值為不顯示此狀態資訊。 [(/LTCG](ltcg-link-time-code-generation.md):狀態*LTCG:無狀態)

### <a name="prevent-dll-binding"></a>防止 DLL 繫結

[/ALLOWBIND](allowbind-prevent-dll-binding.md):NO 在 DLL 的標頭中設置一個位,指示 Bind.exe 不允許綁定圖像。 如果 DLL 已數位簽署，您便可能不想要繫結 DLL (繫結會使簽章無效)。

### <a name="treat-linker-warning-as-errors"></a>將連結器警告視為錯誤

[/WX](wx-treat-linker-warnings-as-errors.md)會導致在連結器生成警告時不會生成輸出檔。

### <a name="force-file-output"></a>強制檔案輸出

[/FORCE](force-force-file-output.md)選項告訴連結器創建 .exe 檔或 DLL,即使符號被引用但未定義,或者是乘以定義的。 它可能建立無效的 .exe 檔案。

**Choices**

- **啟用**- /FORCE,沒有參數意味著多重和未解決。
- **僅將定義的符號相乘**- 使用 /FORCE:MULTI 創建輸出檔,即使 LINK 為符號找到多個定義也是如此。
- **僅未定義符號**- 使用 /FORCE:UNRESOLVED創建輸出檔,無論 LINK 是否找到未定義的符號。 /FORCE:如果入口點符號未解析,則忽略 UNRESOLVED。

### <a name="create-hot-patchable-image"></a>建立熱可修補影像

準備用於熱修補的圖像。

**Choices**

- **已啟用**- 準備用於熱修補的圖像。
- **僅限 X86 圖像**- 準備 X86 圖像進行熱修補。
- **僅限 X64 圖像**- 準備 X64 圖像進行熱修補。
- **只將 Itanium 影像**- 準備用於熱修補的 Itanium 圖像。

### <a name="specify-section-attributes"></a>指定節屬性

[/SECTION](section-specify-section-attributes.md)選項更改節的屬性,在編譯節的 .obj 檔時重寫屬性集。

## <a name="input-property-page"></a>輸入屬性頁

### <a name="additional-dependencies"></a>其他相依性

指定要加入連結指令列的其他項目,例如*內核32.lib*。

### <a name="ignore-all-default-libraries"></a>忽略所有預設函式庫

[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)選項告訴連結器在解析外部引用時從它搜索的庫清單中刪除一個或多個預設庫。

### <a name="ignore-specific-default-libraries"></a>忽略特定的預設程式庫

指定要忽略的一或多個預設程式庫名稱。 使用分號分隔多個庫。 (/NODEFAULTLIB:[名稱,名稱,...]

### <a name="module-definition-file"></a>模組定義檔案

[/DEF](def-specify-module-definition-file.md)選項將模組定義檔 (.def) 傳遞給連結器。 只能指定一個 .def 檔案到 LINK。

### <a name="add-module-to-assembly"></a>新增模組加入到載入

[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)選項允許您向程式集添加模組引用。 模組中的類型資訊將不適用於添加模組引用的程式集程式。 但是,模組中的類型資訊將可用於引用程式集的任何程式。

### <a name="embed-managed-resource-file"></a>嵌入託管資源檔案

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)在輸出檔中嵌入資源檔。

### <a name="force-symbol-references"></a>強制符號參考

[/INCLUDE](include-force-symbol-references.md)選項告訴連結器向符號表添加指定的符號。

### <a name="delay-loaded-dlls"></a>延遲載入的 DLL

[/DELAYLOAD](delayload-delay-load-import.md)選項會導致 DLL 載入延遲。 dll 名稱指定用於延遲載入的 DLL。

### <a name="assembly-link-resource"></a>程式組連結資源

[/ASSEMBLYLINKRESOURCE 選項](assemblylinkresource-link-to-dotnet-framework-resource.md)在輸出檔中創建指向 .NET 框架資源的連結;資源檔未放置在輸出檔中。

## <a name="manifest-file-property-page"></a>清單檔案屬性頁

### <a name="generate-manifest"></a>產生清單

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)指定連結器應建立並排清單檔。

### <a name="manifest-file"></a>清單檔案

[/MANIFESTFILE](manifestfile-name-manifest-file.md)允許您更改清單檔的預設名稱。 清單檔的預設名稱是附加 .manifest 的檔名。

### <a name="additional-manifest-dependencies"></a>其他清單依賴項

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)允許您指定將放置在清單文件的依賴項部分的屬性。

### <a name="allow-isolation"></a>允許隔離

指定資訊清單查閱的行為。 [(/允許隔離](allowisolation-manifest-lookup.md):否)

### <a name="enable-user-account-control-uac"></a>開啟使用者帳戶控制 (UAC)

指定是否啟用使用者帳戶控制。  (/***************************************[ ](manifestuac-embeds-uac-information-in-manifest.md)

### <a name="uac-execution-level"></a>UAC 執行層級

使用使用者帳戶控制時為應用程式指定請求的執行級別。  (/MANIFESTUAC:級別=值*)

**Choices**

- **asInvoker** - UAC 執行等級:作為呼叫器。
- **最高可用 -** UAC 執行級別:最高可用。
- **需要管理員**- UAC 執行級別:需要管理員。

### <a name="uac-bypass-ui-protection"></a>UAC 旁路 UI 保護

指定是否繞過桌面上其他視窗的使用者介面保護級別。  僅為輔助功能應用程式將此屬性設置為"是」。  [(/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccess_true = 假])

## <a name="debugging-property-page"></a>偵錯屬性頁

### <a name="generate-debug-info"></a>產生除錯資訊

此選項允許為 .exe 檔案或 DLL 創建除錯資訊。

**Choices**

- **否**- 不生成調試資訊。
- **生成除錯資訊**-創建完整的程式資料庫 (PDB),非常適合分發到 Microsoft 符號伺服器。
- **生成針對更快連結優化的調試資訊**- 生成程式資料庫 (PDB),非常適合編輯連結-調試週期。
- **生成針對共用和發佈優化的調試資訊**- 生成程式資料庫 (PDB),非常適合編輯連結-調試週期。

### <a name="generate-program-database-file"></a>產生程式資料庫檔案

默認情況下,當指定[/DEBUG](debug-generate-debug-info.md)時,連結器將創建一個程式資料庫 (PDB),該資料庫包含調試資訊。 PDB 的預設檔名具有程式的基本名稱和擴展名 .pdb。

### <a name="strip-private-symbols"></a>剝離專用符號

[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)選項在使用生成 PDB 檔的任何編譯器或連結器選項(/DEBUG、/Z7、/Zd 或 /Zi)構建程式映射時創建第二個程式資料庫 (PDB) 檔。

### <a name="generate-map-file"></a>產生對應檔

[/MAP](map-generate-mapfile.md)選項告訴連結器創建地圖檔。

### <a name="map-file-name"></a>對應檔案名稱

地圖檔的使用者指定名稱。 它替換預設名稱。

### <a name="map-exports"></a>地圖匯出

[/MAPINFO](mapinfo-include-information-in-mapfile.md)選項告訴連結器在地圖檔中包含指定的資訊,如果指定 /MAP 選項,將創建該映射檔。 EXPORT 告訴連結器包括導出的函數。

### <a name="debuggable-assembly"></a>可除錯程式集

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)發出調試屬性屬性,通過調試資訊跟蹤並禁用 JIT 優化。

## <a name="system-property-page"></a>系統屬性頁

### <a name="subsystem"></a>子系統

[/SUBSYSTEM](subsystem-specify-subsystem.md)選項告訴作業系統如何運行 .exe 檔。 子系統的選擇會影響連結器將選擇的入口點符號(或入口點函數)。

**Choices**

- **未設定**- 未設定子系統。
- **主控台**- Win32字元模式應用程式。 主控台應用程式由作業系統提供主控台。 如果定義了主控或 wmain,則"CONSOLE"是預設值。
- **Windows** - 應用程式不需要控制台,可能是因為它創建自己的視窗與使用者交互。 如果定義了 WinMain 或 wWinMain,則「WINDOWS」是預設值。
- **本機**- Windows NT 的設備驅動程式。 如果指定 /DRIVER:WDM,則本機為預設值。
- **EFI 應用程式**- EFI 應用程式。
- **EFI 引導服務驅動程式**- EFI 引導服務驅動程式。
- **EFI ROM** - EFI ROM。
- **EFI 執行時**- EFI 執行時。
- **POSIX** - 在 Windows NT 中使用 POSIX 子系統運行的應用程式。

### <a name="minimum-required-version"></a>最低所需版本

指定子系統的最小所需版本。 參數是範圍 0 到 65,535 中的十進位數位。

### <a name="heap-reserve-size"></a>堆保留大小

指定虛擬記憶體中的堆分配總大小。 默認值為 1 MB。    [(/HEAP:](heap-set-heap-size.md)保留)

### <a name="heap-commit-size"></a>堆提交大小

指定物理記憶體中的堆分配總大小。 默認值為 4 KB。    [(/HEAP](heap-set-heap-size.md):保留,提交)

### <a name="stack-reserve-size"></a>堆疊保留大小

指定虛擬記憶體中的堆疊配置大小總和。 默認值為 1 MB。     [(/STACK:](stack-stack-allocations.md)保留)

### <a name="stack-commit-size"></a>堆疊提交大小

指定物理記憶體中的總堆疊分配大小。 默認值為 4 KB。     [(/STACK:](stack-stack-allocations.md)保留,提交)

### <a name="enable-large-addresses"></a>開啟大位址

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)選項告訴連結器應用程式可以處理大於 2 GB 的位址。 默認情況下,/LARGEADDRESSAWARE:如果在鏈接器線路上未以其他方式指定 /LARGEADDRESSAWARE,則啟用"否"。

### <a name="terminal-server"></a>終端伺服器

[/TSAWARE](tsaware-create-terminal-server-aware-application.md)選項在程式圖像的可選標題中的IMAGE_OPTIONAL_HEADER Dll特色欄位中設置標誌。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

### <a name="swap-run-from-cd"></a>從 CD 交換執行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)選項告訴操作系統首先將連結器輸出複製到交換檔,然後從那裡運行映射。 此選項是 Windows NT 4.0(及更高版本)功能。 指定**CD**後,作業系統會將可移動磁碟上的映像複製到頁面檔,然後載入它。

### <a name="swap-run-from-network"></a>從網路交換執行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)選項告訴操作系統首先將連結器輸出複製到交換檔,然後從那裡運行映射。 此選項是 Windows NT 4.0(及更高版本)功能。 如果指定**了 NET,** 作業系統將首先將二進位映像從網路複製到交換檔,並從那裡載入該檔。 此選項可用於通過網路運行應用程式。

### <a name="driver"></a>驅動程式

使用[/DRIVER](driver-windows-nt-kernel-mode-driver.md)連結器選項生成 Windows NT 內核模式驅動程式。

**Choices**

- **未設定**- 預設驅動程式設定。
- **驅動程式**─驅動程式
- **僅限 UP** - /DRIVER:UPONLY 使連結器將IMAGE_FILE_UP_SYSTEM_ONLY位添加到輸出標頭中的特徵,以指定它是單處理器 (UP) 驅動程式。 操作系統將拒絕在多處理器 (MP) 系統上載入 UP 驅動程式。
- **WDM** - /DRIVER:WDM 使連結器在可選標頭的 Dll特徵欄位中設置IMAGE_DLLCHARACTERISTICS_WDM_DRIVER位。

## <a name="optimization-property-page"></a>優化屬性頁

### <a name="references"></a>參考

[/OPT](opt-optimizations.md):REF 消除了從未引用的函數和/或數據,而 /OPT:NOREF 保留從未引用的函數和/或數據。

### <a name="enable-comdat-folding"></a>啟用 COMDAT 摺疊

使用[/OPT](opt-optimizations.md):ICF\[[反覆運算] 執行相同的 COMDAT 摺疊。

### <a name="function-order"></a>功能順序

[/ORDER](order-put-functions-in-order.md)選項告訴 LINK 以預定的順序將某些 COMDAT 放入映射中來優化程式。 LINK 在圖像中的每個部分中按指定順序放置函數。

### <a name="profile-guided-database"></a>設定檔案開機資料庫

為設定檔引導優化指定 .pgd 檔。 ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>連結時產生程式碼

指定連結時產生程式碼。 ([/LTCG](ltcg-link-time-code-generation.md))

**Choices**

- **預設值**- 預設 LTCG 設定。
- **使用快速連結時間代碼產生**- 使用連結時間代碼產生與[/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。
- **使用連結時間代碼產生**- 使用[連結時間代碼產生](ltcg-link-time-code-generation.md)。
- **設定檔案開機 - 儀器**-[使用 :PGINSTRUMENT 的設定檔導取最佳化](../profile-guided-optimizations.md)。
- **設定檔案引導最佳化 - 最佳化**- 指定連結器應使用執行檢測的二進位檔案後創建的設定檔資料來創建優化的圖像。
- **設定檔案引導優化 - 更新**- 允許並追蹤從 :PGINSTRUMENT 階段中指定的內容添加或修改的輸入檔案清單。

## <a name="embedded-idl-property-page"></a>嵌入式 IDL 屬性頁

### <a name="midl-commands"></a>MIDL 指令

指定 MIDL 命令列選項。 ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>忽略嵌入式識別碼

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)選項指定原始碼中的任何 IDL 屬性都不應處理到 .idl 檔中。

### <a name="merged-idl-base-file-name"></a>合併的識別碼檔名稱

[/IDLOUT](idlout-name-midl-output-files.md)選項指定 .idl 檔案的名稱和副檔名。

### <a name="type-library"></a>類型庫

[/TLBOUT](tlbout-name-dot-tlb-file.md)選項指定 .tlb 檔案的名稱和副檔名。

### <a name="typelib-resource-id"></a>類型 Lib 資源識別碼

允許您指定連結器生成的類型庫的資源 ID。 [(/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>視窗中繼資料屬性頁

### <a name="generate-windows-metadata"></a>產生 Windows 中繼資料

啟用或禁用生成 Windows 中繼資料。

**Choices**

- **是**- 啟用生成 Windows 中繼資料檔。
- **否**- 停用生成 Windows 中繼資料檔。

### <a name="windows-metadata-file"></a>視窗中繼資料檔案

[/WINMDFILE](winmdfile-specify-winmd-file.md)選項開關。

### <a name="windows-metadata-key-file"></a>Windows 中繼資料金鑰檔

指定鍵或金鑰對以對 Windows 中繼資料進行簽名。 [(/溫德基檔案](winmdkeyfile-specify-winmd-key-file.md):檔名)

### <a name="windows-metadata-key-container"></a>視窗中繼資料金鑰容器

指定一個鍵容器來對 Windows 中繼資料進行簽名。 [(/溫德基:](winmdkeycontainer-specify-key-container.md)姓名)

### <a name="windows-metadata-delay-sign"></a>視窗中繼資料延遲符號

部分簽名 Windows 中數據。 如果您只想將公開金鑰放在 Windows 中,請使用[/WINMDDELAYSIGN。](winmddelaysign-partially-sign-a-winmd.md) 默認值為 /WINMDDELAYSIGN:否。

## <a name="advanced-property-page"></a>進階屬性頁

### <a name="entry-point"></a>進入點

[/ENTRY](entry-entry-point-symbol.md)選項指定入口點函數作為 .exe 檔案或 DLL 的起始位址。

### <a name="no-entry-point"></a>沒有入口點

建立僅資源 DLL 需要[/NOENTRY](noentry-no-entry-point.md)選項。使用此選項可防止 LINK`_main`將引用 連結到 DLL。

### <a name="set-checksum"></a>設定檢查與

[/RELEASE](release-set-the-checksum.md)選項在 .exe 文件的頭部設置校驗和。

### <a name="base-address"></a>基底位址

設定程式的基底位址。 [(/BASE](base-base-address.md):\[位址 ,大小] |@filename鍵")

### <a name="randomized-base-address"></a>隨機基本位址

隨機基本位址。 [(/動態基礎](dynamicbase-use-address-space-layout-randomization.md)\[:否])

### <a name="fixed-base-address"></a>固定基本位址

建立僅可在其慣用基底位址載入的程式。 [(/固定](fixed-fixed-base-address.md)\[:否*)

### <a name="data-execution-prevention-dep"></a>資料執行防止 (DEP)

將可執行檔標記為已測試為與 Windows 數據執行預防功能相容。 [(/NXcompat](nxcompat-compatible-with-data-execution-prevention.md)\[:否])

### <a name="turn-off-assembly-generation"></a>關閉元件產生

[/NOASSEMBLY](noassembly-create-a-msil-module.md)選項告訴連結器為當前輸出文件創建圖像,而不使用 .NET Framework 程式集。

### <a name="unload-delay-loaded-dll"></a>卸載載入的延遲 DLL

**UNLOAD**修飾詞告訴延遲載入說明器函數以支援 DLL 的顯式卸載。 [(/延遲](delay-delay-load-import-settings.md):卸載)

### <a name="nobind-delay-loaded-dll"></a>未結合延遲載入 DLL

**NOBIND**限定符告訴連結器不要在最終圖像中包含可綁定的 IAT。 預設會是針對延遲載入 DLL 建立可繫結 IAT。 [(/延遲](delay-delay-load-import-settings.md):不綁定)

### <a name="import-library"></a>匯入程式庫

覆寫預設匯入程式庫名稱。 [(/IMPLIB](implib-name-import-library.md):檔案名稱)

### <a name="merge-sections"></a>合併節

[/MERGE](merge-combine-sections.md)選項將第一部分(來自)和第二部分(到)合併,將生成的部分命名為 例如,/合併:.rdata_.text。

### <a name="target-machine"></a>目標機器

[/MACHINE](machine-specify-target-platform.md)選項指定程式的目標平臺。

**Choices**

- **未設定**
- **機器ARM**
- **機器ARM64**
- **機機**
- **機器IA64**
- **機器MIPS**
- **機器MIPS16**
- **機器MIPSFPU**
- **機器MIPSFPU16**
- **機器SH4**
- **機器**
- **機器X64**
- **機器X86**

### <a name="profile"></a>設定檔

產生可與效能工具分析工具搭配使用的輸出檔。 需要設定生成除錯資訊 (/[/DEBUG)。](debug-generate-debug-info.md) ([/簡介](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR 執行緒屬性

顯式指定 CLR 程式入口點的線程屬性。

**Choices**

- **MTA 執行緒屬性**- 將 MTAThreadAttribute 屬性應用於程式的入口點。
- **STA 執行緒屬性**- 將 STAThreadAttribute 屬性應用於程式的入口點。
- **默認執行緒屬性**- 與未指定[/CLRTHREAD 屬性](clrthreadattribute-set-clr-thread-attribute.md)相同。 讓通用語言運行時 (CLR) 設置預設線程屬性。

### <a name="clr-image-type"></a>CLR 影像類型

設定 CLR 映像的類型 (IJW、純或安全)。

**Choices**

- **強制 IJW 影像**
- **強制純 IL 影像**
- **強制安全的品質**
- **預設影像類型**

### <a name="key-file"></a>金鑰檔

指定鍵或鍵對以對程式集進行簽名。 [(/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):檔案名)

### <a name="key-container"></a>金鑰容器

指定要對程式集進行簽名的鍵容器。 [(/鍵式](keycontainer-specify-a-key-container-to-sign-an-assembly.md):姓名)

### <a name="delay-sign"></a>延遲符號

對程式集進行部分簽名。 如果只想將公開金鑰放在程式集中,請使用[/DELAYSIGN。](delaysign-partially-sign-an-assembly.md) 默認值為 /DELAYSIGN:否。

### <a name="clr-unmanaged-code-check"></a>CLR 非託管代碼檢查

[/CLRUN管理代碼檢查](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)指定連結器是否將禁止解壓縮 Un 託管代碼安全屬性應用於從託管代碼連結到本機 DLL 的 Pler 生成的 PInvoke 調用。

### <a name="error-reporting"></a>錯誤報告

讓您直接提供內部編譯器錯誤 (ICE) 資訊給 Visual C++ 團隊。

**Choices**

- **立即提示**- 立即提示。
- **下一個登錄佇列**- 下一個登錄佇列。
- **傳送錯誤報告**- 傳送錯誤報告。
- **沒有錯誤報告**─ 錯誤報告。

### <a name="sectionalignment"></a>SectionAlignment

[/ALIGN](align-section-alignment.md)選項指定程式線性位址空間中每個部分的對齊方式。 數位參數以位元組為單位,並且必須是2的電源。

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>保留 PInvoke 呼叫的最後錯誤代碼

[/CLRSUPPORTLASTERROR(](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)預設情況下處於打開狀態)保留了通過 P/Invoke 機制調用的函數的最後錯誤代碼,該機制允許您從使用 /clr 編譯的代碼調用 DLLS 中的本機函數。

**Choices**

- **已啟用**- 啟用 CLR 支援 Last 錯誤。
- **關閉**- 停用 CLR 支援 Last 錯誤。
- **僅限系統 Dlls** - 僅啟用 CLRSupport LastError。

### <a name="image-has-safe-exception-handlers"></a>映射具有安全異常處理程式

指定[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)後,連結器僅當還可以生成映射的安全異常處理程序的表時才會生成映射。 此表為作業系統指定異常處理程式對映射有效。
