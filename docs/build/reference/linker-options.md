---
title: MSVC 連結器選項
description: Microsoft LINK 連結器所支援的選項清單。
ms.date: 09/24/2019
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 23cd1c3ce767cf8046e3439432db795f032dc370
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685581"
---
# <a name="linker-options"></a>連結器選項

LINK.exe 會連結通用物件檔案格式 (COFF) 物件檔案及程式庫，以建立可執行檔 (.exe) 或動態連結程式庫 (DLL)。

下表列出 LINK.exe 的選項。 如需 LINK 的詳細資訊，請參閱：

- [編譯器控制的 LINK 選項](compiler-controlled-link-options.md)

- [LINK 輸入檔](link-input-files.md)

- [LINK 輸出](link-output.md)

- [保留字](reserved-words.md)

在命令列上，連結器選項不區分大小寫;例如，/base 和/BASE 表示相同的事物。 如需有關如何命令列或在 Visual Studio 中指定每個選項的詳細資訊，請參閱該選項的文件。

您可以使用 [comment](../../preprocessor/comment-c-cpp.md) pragma，來指定部分連結器選項。

## <a name="linker-options-listed-alphabetically"></a>依字母順序列出連結器選項

|選項|用途|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|指定回應檔。|
|[/ALIGN](align-section-alignment.md)|指定每一個區段的對齊情況。|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|指定不能繫結 DLL。|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|指定資訊清單查閱的行為。|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|指定應用程式是否必須在 appcontainer 處理序環境中執行。|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|將 <xref:System.Diagnostics.DebuggableAttribute> 加入至 Managed 映像檔。|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|建立與 Managed 資源的連結。|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|指定 Microsoft 中繼語言 (MSIL) 模組應該匯入至組件。|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|將 Managed 資源內嵌至組件中。|
|[/BASE](base-base-address.md)|設定程式的基底位址。|
|[/CGTHREADS](cgthreads-compiler-threads.md)|設定在指定連結時間程式碼產生時，要用於最佳化及程式碼產生的 cl.exe 執行緒數目。|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|設定 CLR 映像的類型 (IJW、純或安全)。|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼。|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|指定要套用至 CLR 程式進入點的 threading 屬性。|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|指定連結器是否將 SuppressUnmanagedCodeSecurity 屬性套用至連結器產生的 PInvoke Stub，這些 Stub 會從 Managed 程式碼呼叫至原生 DLL。|
|[/DEBUG](debug-generate-debug-info.md)|建立偵錯資訊。|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|指定要包含在偵錯資訊的資料。|
|[/DEF](def-specify-module-definition-file.md)|將模組定義 (.def) 檔傳遞至連結器。|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|解析外部參考時，搜尋指定的程式庫。|
|[/DELAY](delay-delay-load-import-settings.md)|控制 DLL 的延遲載入。|
|[/DELAYLOAD](delayload-delay-load-import.md)|引起指定之 DLL 的延遲載入。|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|部分簽署組件。|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|設定相依 DLL 負載的預設旗標。|
|[/DLL](dll-build-a-dll.md)|建置 DLL。|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|建立核心模式驅動程式。|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|指定是否產生可執行映像檔，其可使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重定基底。|
|[/ENTRY](entry-entry-point-symbol.md)|設定開始位址。|
|[/errorReport](errorreport-report-internal-linker-errors.md)|將內部連結器錯誤報告給 Microsoft。|
|[/EXPORT](export-exports-a-function.md)|匯出函式。|
|[/FILEALIGN](filealign.md)|將輸出檔案中的區段對齊指定值的倍數。|
|[/FIXED](fixed-fixed-base-address.md)|建立僅可在其慣用基底位址載入的程式。|
|[/FORCE](force-force-file-output.md)|強制連結完成，即使存在未解析的符號或符號定義多次也一樣。|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|建立可熱修補的映像檔。|
|[/GENPROFILE、/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|這兩個選項都指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 /GENPROFILE 和 /FASTGENPROFILE 使用不同的預設參數。|
|[/GUARD](guard-enable-guard-checks.md)|啟用「控制流程防護」防護。|
|[/HEAP](heap-set-heap-size.md)|設定堆積的大小 (以位元組為單位)。|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|指定支援高熵 64 位元位址空間配置隨機載入 (ASLR)。|
|[/IDLOUT](idlout-name-midl-output-files.md)|指定 .idl 檔案和其他 MIDL 輸出檔的名稱。|
|[/IGNORE](ignore-ignore-specific-warnings.md)|隱藏指定連結器警告的輸出。|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|防止將屬性資訊處理至 .idl 檔案。|
|[/IMPLIB](implib-name-import-library.md)|覆寫預設匯入程式庫名稱。|
|[/INCLUDE](include-force-symbol-references.md)|強制執行符號參考。|
|[/INCREMENTAL](incremental-link-incrementally.md)|控制累加連結。|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|指定模組在載入時需要進行簽章檢查。|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|指定用於簽署組件的金鑰容器。|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|指定用於簽署組件的金鑰或金鑰組。|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|告知編譯器應用程式支援比 2 GB 更大的位址。|
|[/LIBPATH](libpath-additional-libpath.md)|指定要在環境程式庫路徑之前搜尋的路徑。|
|[/LINKREPRO](linkrepro.md)|指定在中產生連結重現成品的路徑。|
|[/LINKREPROTARGET](linkreprotarget.md)|只有在產生指定的目標時，才會產生連結重現。|
|[/LTCG](ltcg-link-time-code-generation.md)|指定連結時產生程式碼。|
|[/MACHINE](machine-specify-target-platform.md)|指定目標平台。|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|建立並存資訊清單檔，並選擇性地將其內嵌於二進位檔中。|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|指定資訊清單檔中的 @no__t 0dependentAssembly > 區段。|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|變更資訊清單檔的預設名稱。|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|指定連結器的資訊清單輸入檔，以在二進位檔中處理並內嵌於二進位檔中。 您可以多次使用此選項，以指定多個資訊清單輸入檔。|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|指定使用者帳戶控制 (UAC) 資訊是否內嵌於程式資訊清單中。|
|[/MAP](map-generate-mapfile.md)|建立對應檔 (Mapfile)。|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|在對應檔中包括指定的資訊。|
|[/MERGE](merge-combine-sections.md)|結合區段。|
|[/MIDL](midl-specify-midl-command-line-options.md)|指定 MIDL 命令列選項。|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|將 Natvis 檔中的偵錯工具視覺化檢視加入 PDB。|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|不建立 .NET Framework 組件。|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|當解析外部參考時，忽略所有 (或指定的) 預設程式庫。|
|[/NOENTRY](noentry-no-entry-point.md)|建立僅含資源的 DLL。|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|隱藏啟始橫幅。|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|將可執行檔標記為已驗證與 Windows 資料執行防止功能相容。|
|[/OPT](opt-optimizations.md)|控制 LINK 最佳化。|
|[/ORDER](order-put-functions-in-order.md)|以預先定義的順序，將 COMDAT 放入映像檔。|
|[/OUT](out-output-file-name.md)|指定輸出檔名稱。|
|[/PDB](pdb-use-program-database.md)|建立程式資料庫 (PDB) 檔。|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|使用替代位置儲存 PDB 檔。|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|建立沒有專用符號的程式資料庫 (PDB) 檔。|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|指定 .pgd 檔用於特性指引最佳化。|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|已**過時**建立安全線程的 PGO 檢測組建。|
|[/PROFILE](profile-performance-tools-profiler.md)|產生可與效能工具分析工具搭配使用的輸出檔。|
|[/RELEASE](release-set-the-checksum.md)|在 .exe 標頭中設定總和檢查。|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|指定映像檔將包含安全例外狀況處理常式的表格。|
|[/SECTION](section-specify-section-attributes.md)|覆寫區段的屬性。|
|[/SOURCELINK](sourcelink.md)|指定要加入 PDB 的 SourceLink 檔案。|
|[/STACK](stack-stack-allocations.md)|設定堆疊的大小 (以位元組為單位)。|
|[/STUB](stub-ms-dos-stub-file-name.md)|將 MS-DOS Stub 程式附加至 Win32 程式。|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|告知作業系統如何執行 .exe 檔。|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|告知作業系統在執行連結器輸出之前，先將其複製到交換檔。|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|指定連結器產生類型程式庫的資源 ID。|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|指定 .tlb 檔案和其他 MIDL 輸出檔的名稱。|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|建立專門設計用來在終端伺服器下執行的應用程式。|
|[/USEPROFILE](useprofile.md)|使用特性指引優化訓練資料來建立優化的影像。|
|[/VERBOSE](verbose-print-progress-messages.md)|列印連結器進度訊息。|
|[/VERSION](version-version-information.md)|指派版本號碼。|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|包含指定靜態程式庫中的每個物件檔案。|
|[/WINMD](winmd-generate-windows-metadata.md)|啟用 Windows 執行階段中繼資料檔的產生。|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|指定由 [/WINMD](winmd-generate-windows-metadata.md) 連結器選項所產生之 Windows 執行階段中繼資料 (winmd) 輸出檔的名稱。|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|指定用於簽署 Windows 執行階段中繼資料的金鑰或金鑰組。|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|指定用於簽署 Windows 中繼資料檔的金鑰容器。|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|透過將公開金鑰置於 Windows 執行階段中繼資料 (.winmd) 檔中，來部分地簽署 winmd 檔。|
|[/WX](wx-treat-linker-warnings-as-errors.md)|將連結器警告視為錯誤。|

如需詳細資訊，請參閱 [Compiler-Controlled LINK Options](compiler-controlled-link-options.md)。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)\
[MSVC 連結器參考](linking.md)
