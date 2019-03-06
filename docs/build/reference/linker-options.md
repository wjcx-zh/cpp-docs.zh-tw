---
title: 連結器選項
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 63cfa784242af1f737c116629a29be5ad77af31d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415197"
---
# <a name="linker-options"></a>連結器選項

LINK.exe 會連結通用物件檔案格式 (COFF) 物件檔案及程式庫，以建立可執行檔 (.exe) 或動態連結程式庫 (DLL)。

下表列出 LINK.exe 的選項。 如需 LINK 的詳細資訊，請參閱：

- [編譯器控制的 LINK 選項](../../build/reference/compiler-controlled-link-options.md)

- [LINK 輸入檔](../../build/reference/link-input-files.md)

- [LINK 輸出](../../build/reference/link-output.md)

- [保留字](../../build/reference/reserved-words.md)

在命令列中，連結器選項不區分大小寫;例如 /base 與 /BASE 意義相同。 如需有關如何命令列或在 Visual Studio 中指定每個選項的詳細資訊，請參閱該選項的文件。

您可以使用 [comment](../../preprocessor/comment-c-cpp.md) pragma，來指定部分連結器選項。

|選項|用途|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|指定回應檔。|
|[/ALIGN](../../build/reference/align-section-alignment.md)|指定每一個區段的對齊情況。|
|[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|指定不能繫結 DLL。|
|[/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|指定資訊清單查閱的行為。|
|[/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|指定應用程式是否必須在 appcontainer 處理序環境中執行。|
|[/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|將 <xref:System.Diagnostics.DebuggableAttribute> 加入至 Managed 映像檔。|
|[/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|建立與 Managed 資源的連結。|
|[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|指定 Microsoft 中繼語言 (MSIL) 模組應該匯入至組件。|
|[/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|將 Managed 資源內嵌至組件中。|
|[/BASE](../../build/reference/base-base-address.md)|設定程式的基底位址。|
|[/CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|設定在指定連結時間程式碼產生時，要用於最佳化及程式碼產生的 cl.exe 執行緒數目。|
|[/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|設定 CLR 映像的類型 (IJW、純或安全)。|
|[/CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼。|
|[/CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|指定要套用至 CLR 程式進入點的 threading 屬性。|
|[/CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|指定連結器是否將 SuppressUnmanagedCodeSecurity 屬性套用至連結器產生的 PInvoke Stub，這些 Stub 會從 Managed 程式碼呼叫至原生 DLL。|
|[/DEBUG](../../build/reference/debug-generate-debug-info.md)|建立偵錯資訊。|
|[/DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|指定要包含在偵錯資訊的資料。|
|[/DEF](../../build/reference/def-specify-module-definition-file.md)|將模組定義 (.def) 檔傳遞至連結器。|
|[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|解析外部參考時，搜尋指定的程式庫。|
|[/DELAY](../../build/reference/delay-delay-load-import-settings.md)|控制 DLL 的延遲載入。|
|[/DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|引起指定之 DLL 的延遲載入。|
|[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|部分簽署組件。|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|設定相依的 DLL 載入預設旗標。|
|[/DLL](../../build/reference/dll-build-a-dll.md)|建置 DLL。|
|[/DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|建立核心模式驅動程式。|
|[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|指定是否產生可執行映像檔，其可使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重定基底。|
|[/ENTRY](../../build/reference/entry-entry-point-symbol.md)|設定開始位址。|
|[/errorReport](../../build/reference/errorreport-report-internal-linker-errors.md)|將內部連結器錯誤報告給 Microsoft。|
|[/EXPORT](../../build/reference/export-exports-a-function.md)|匯出函式。|
|[/FILEALIGN](../../build/reference/filealign.md)|將在指定的值的倍數與輸出檔案內區段的對齊。|
|[/FIXED](../../build/reference/fixed-fixed-base-address.md)|建立僅可在其慣用基底位址載入的程式。|
|[/FORCE](../../build/reference/force-force-file-output.md)|強制連結完成，即使存在未解析的符號或符號定義多次也一樣。|
|[/FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|建立可熱修補的映像檔。|
|[/GENPROFILE、/FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|這兩個選項都指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 /GENPROFILE 和 /FASTGENPROFILE 使用不同的預設參數。|
|[/GUARD](../../build/reference/guard-enable-guard-checks.md)|啟用「控制流程防護」防護。|
|[/HEAP](../../build/reference/heap-set-heap-size.md)|設定堆積的大小 (以位元組為單位)。|
|[/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|指定支援高熵 64 位元位址空間配置隨機載入 (ASLR)。|
|[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|指定 .idl 檔案和其他 MIDL 輸出檔的名稱。|
|[/IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|隱藏指定連結器警告的輸出。|
|[/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|防止將屬性資訊處理至 .idl 檔案。|
|[/IMPLIB](../../build/reference/implib-name-import-library.md)|覆寫預設匯入程式庫名稱。|
|[/INCLUDE](../../build/reference/include-force-symbol-references.md)|強制執行符號參考。|
|[/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|控制累加連結。|
|[/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|指定模組在載入時需要進行簽章檢查。|
|[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|指定用於簽署組件的金鑰容器。|
|[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|指定用於簽署組件的金鑰或金鑰組。|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|告知編譯器應用程式支援比 2 GB 更大的位址。|
|[/LIBPATH](../../build/reference/libpath-additional-libpath.md)|指定要在環境程式庫路徑之前搜尋的路徑。|
|[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)|指定連結時產生程式碼。|
|[/MACHINE](../../build/reference/machine-specify-target-platform.md)|指定目標平台。|
|[/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|建立並存資訊清單檔，並選擇性地將其內嵌於二進位檔中。|
|[/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|指定\<dependentAssembly > 一節中的資訊清單檔案。|
|[/MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|變更資訊清單檔的預設名稱。|
|[/MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|指定連結器的資訊清單輸入檔，以在二進位檔中處理並內嵌於二進位檔中。 您可以多次使用此選項，以指定多個資訊清單輸入檔。|
|[/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|指定使用者帳戶控制 (UAC) 資訊是否內嵌於程式資訊清單中。|
|[/MAP](../../build/reference/map-generate-mapfile.md)|建立對應檔 (Mapfile)。|
|[/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|在對應檔中包括指定的資訊。|
|[/MERGE](../../build/reference/merge-combine-sections.md)|結合區段。|
|[/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|指定 MIDL 命令列選項。|
|[/NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|從.natvis 檔案加入 PDB 偵錯工具視覺化檢視。|
|[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|不建立 .NET Framework 組件。|
|[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|當解析外部參考時，忽略所有 (或指定的) 預設程式庫。|
|[/NOENTRY](../../build/reference/noentry-no-entry-point.md)|建立僅含資源的 DLL。|
|[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|隱藏啟始橫幅。|
|[/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|將可執行檔標記為已驗證與 Windows 資料執行防止功能相容。|
|[/OPT](../../build/reference/opt-optimizations.md)|控制 LINK 最佳化。|
|[/ORDER](../../build/reference/order-put-functions-in-order.md)|以預先定義的順序，將 COMDAT 放入映像檔。|
|[/OUT](../../build/reference/out-output-file-name.md)|指定輸出檔名稱。|
|[/PDB](../../build/reference/pdb-use-program-database.md)|建立程式資料庫 (PDB) 檔。|
|[/PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|使用替代位置儲存 PDB 檔。|
|[/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|建立沒有專用符號的程式資料庫 (PDB) 檔。|
|[/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|指定 .pgd 檔用於特性指引最佳化。|
|[/POGOSAFEMODE](../../build/reference/pogosafemode-linker-option.md)|**過時**建立安全執行緒 PGO 檢測建置。|
|[/PROFILE](../../build/reference/profile-performance-tools-profiler.md)|產生可與效能工具分析工具搭配使用的輸出檔。|
|[/RELEASE](../../build/reference/release-set-the-checksum.md)|在 .exe 標頭中設定總和檢查。|
|[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|指定映像檔將包含安全例外狀況處理常式的表格。|
|[/SECTION](../../build/reference/section-specify-section-attributes.md)|覆寫區段的屬性。|
|[/SOURCELINK](../../build/reference/sourcelink.md)|指定要加入 PDB SourceLink 檔案。|
|[/STACK](../../build/reference/stack-stack-allocations.md)|設定堆疊的大小 (以位元組為單位)。|
|[/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|將 MS-DOS Stub 程式附加至 Win32 程式。|
|[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|告知作業系統如何執行 .exe 檔。|
|[/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|告知作業系統在執行連結器輸出之前，先將其複製到交換檔。|
|[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|指定連結器產生類型程式庫的資源 ID。|
|[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|指定 .tlb 檔案和其他 MIDL 輸出檔的名稱。|
|[/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|建立專門設計用來在終端伺服器下執行的應用程式。|
|[/USEPROFILE](../../build/reference/useprofile.md)|若要建立最佳化的映像的使用特性指引最佳化定型資料。|
|[/VERBOSE](../../build/reference/verbose-print-progress-messages.md)|列印連結器進度訊息。|
|[/VERSION](../../build/reference/version-version-information.md)|指派版本號碼。|
|[/WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|包含從指定的靜態程式庫的每個物件檔案。|
|[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)|啟用 Windows 執行階段中繼資料檔的產生。|
|[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|指定由 [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) 連結器選項所產生之 Windows 執行階段中繼資料 (winmd) 輸出檔的名稱。|
|[/WINMDKEYFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|指定用於簽署 Windows 執行階段中繼資料的金鑰或金鑰組。|
|[/WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|指定用於簽署 Windows 中繼資料檔的金鑰容器。|
|[/WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|透過將公開金鑰置於 Windows 執行階段中繼資料 (.winmd) 檔中，來部分地簽署 winmd 檔。|
|[/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|將連結器警告視為錯誤。|

如需詳細資訊，請參閱 [Compiler-Controlled LINK Options](../../build/reference/compiler-controlled-link-options.md)。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[設定連結器選項](../../build/reference/setting-linker-options.md)
