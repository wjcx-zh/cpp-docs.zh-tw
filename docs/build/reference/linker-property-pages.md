---
title: 連結器屬性頁
ms.date: 7/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 17880d50ae012b640cb83f3766883ab2b1bcbe73
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537589"
---
# <a name="linker-property-pages"></a>連結器屬性頁

下列屬性可在 [**專案** > **屬性** > 設定] [**屬性** > **連結器**] 下找到。 如需連結器的詳細資訊, 請參閱 CL 叫用[連結器](cl-invokes-the-linker.md)和[連結器選項](linker-options.md)。

## <a name="general-property-page"></a>一般屬性頁

### <a name="output-file"></a>輸出檔案

[/Out](out-output-file-name.md)選項會覆寫連結器所建立之程式的預設名稱和位置。

### <a name="show-progress"></a>顯示進度

列印連結器進度訊息

**做**

- **未設定**-沒有詳細資訊。
- **顯示所有進度訊息**-顯示所有進度訊息。 
- **針對搜尋**的程式庫-顯示進度訊息, 只指出搜尋的程式庫。
- **關於優化連結期間的 COMDAT 折**迭-顯示優化連結期間 COMDAT 折迭的相關資訊。
- **關於優化連結期間移除的資料**-顯示優化連結期間所移除之函式和資料的相關資訊。
- **關於與 SEH 不相容的模組**-顯示與安全例外狀況處理不相容之模組的相關資訊。
- **關於與 managed 程式碼相關的連結器活動**-顯示與 managed 程式碼相關之連結器活動的資訊。

### <a name="version"></a>版本

[/VERSION](version-version-information.md)選項會指示連結器將版本號碼放在 .exe 或 .dll 檔案的標頭中。 使用 DUMPBIN/HEADERS 查看選擇性標頭值的 [映射版本] 欄位, 以查看 **/VERSION**的效果。

### <a name="enable-incremental-linking"></a>啟用累加連結

啟用增量連結。 ([/INCREMENTAL](incremental-link-incrementally.md),/INCREMENTAL: NO)

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

[/Nologo](nologo-suppress-startup-banner-linker.md)選項可防止顯示著作權訊息和版本號碼。 

### <a name="ignore-import-library"></a>忽略匯入程式庫

這個屬性會告知連結器不要將這個組建所產生的任何 .lib 輸出連結到任何相依專案。 這可讓專案系統處理在建置時不會產生 .lib 檔的 .dll 檔。 如果專案相依於另一個會產生 DLL 的專案，則專案系統會自動連結該個子專案所產生的 .lib 檔。 產生 COM Dll 或資源專用 DLL 的專案可能不需要這點；這些 DLL 沒有任何有意義的匯出。 如果 DLL 沒有任何匯出，連結器便不會產生 .lib 檔。 如果磁碟上沒有任何匯出的 .lib 檔，專案系統會告知連結器連結此 (遺漏的) DLL，連結就會失敗。 請使用 [忽略匯入程式庫] 屬性來解決此問題。 當設定為 [是] 時，專案系統會忽略該 .lib 檔是否存在，並且會導致相依於此專案的任何專案都不要與不存在的 .lib 檔連結。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>登錄輸出

對組建輸出執行 `regsvr32.exe /s $(TargetPath)`，這只有在 .dll 專案上才有效。 對於 .exe 專案，則會忽略這個屬性。 若要註冊 .exe 輸出，請在組態上設定建置後事件，以執行已註冊之 .exe 檔一律需要的自訂登錄。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>個別使用者重新導向

Visual Studio 中的註冊傳統上都在 HKEY_CLASSES_ROOT (HKCR) 進行。 使用 Windows Vista 和更新版本的作業系統，若要存取 HKCR 您必須以提升權限模式執行 Visual Studio。 開發人員不一定想要在提升權限的模式中執行，但仍然必須使用註冊。 個別使用者重新導向，可讓您不需要以此模式執行即可註冊。

個別使用者重新導向會強制將 HKCR 的任何寫入重新導向至 HKEY\_CURRENT\_USER (HKCU)。 如果關閉每個使用者重新導向，它可能會在程式嘗試寫入 HKCR 時導致[專案建置錯誤 PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="additional-library-directories"></a>其他程式庫目錄

允許使用者覆寫環境程式庫路徑。 ([/LIBPATH](libpath-additional-libpath.md): 資料夾)

### <a name="link-library-dependencies"></a>連結程式庫相依性

指定是否要連結由相依專案所產生的 .lib 檔。 一般而言，您會想連結 .lib 檔，但這可能不適用於特定 DLL 的情況。

您也可以提供檔案名稱和相對路徑以指定 .obj 檔案，例如 "..\\..\MyLibProject\MyObjFile.obj"。 如果 .obj 檔案的原始程式碼 #includes 先行編譯標頭檔；例如 pch.h，pch.obj 檔案位於和 MyObjFile.obj 相同的資料夾，而且您也必須新增 pch.obj 作為其他相依性。

### <a name="use-library-dependency-inputs"></a>使用程式庫相依性輸入

指定在連結專案相依性的程式庫輸出時, 是否使用管理員工具的輸入而非程式庫檔案本身。 在大型專案中，當相依專案產生 .lib 檔時，會停用累加連結。 如果有許多相依專案產生 .lib 檔，建置應用程式可能會花很長的時間。 當這個屬性設定為 [是]，專案系統會針對相依專案所產生的 .lib 連結 .obj 檔，進而啟用累加連結。

如需如何存取 [**一般**連結器] 屬性頁的詳細資訊, 請參閱[Visual Studio 中的設定C++編譯器和組建屬性](../working-with-project-properties.md)。

### <a name="link-status"></a>連結狀態

指定連結器是否應該顯示進度指示器, 以顯示連結完成的百分比。 預設為不顯示此狀態資訊。 ([/LTCG](ltcg-link-time-code-generation.md): STATUS |LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>防止 Dll 系結

[/ALLOWBIND](allowbind-prevent-dll-binding.md): NO 會在 DLL 標頭中設定一個位, 表示不允許系結影像。 如果 DLL 已數位簽署，您便可能不想要繫結 DLL (繫結會使簽章無效)。

### <a name="treat-linker-warning-as-errors"></a>將連結器警告視為錯誤

如果連結器產生警告, [/wx](wx-treat-linker-warnings-as-errors.md)不會產生輸出檔。

### <a name="force-file-output"></a>強制檔案輸出

[/Force](force-force-file-output.md)選項會指示連結器建立 .exe 檔或 DLL, 即使符號已被參考但未定義或已進行乘法定義也一樣。 它可能會建立不正確 .exe 檔案。

**做**

- **已啟用**-不含引數的/force 會隱含多個和未解析。
- **僅限定義的符號**-使用/FORCE: MULTIPLE 來建立輸出檔, 不論連結是否為符號尋找一個以上的定義。
- **僅限未定義的符號**-使用/FORCE: 無法解析來建立輸出檔, 不論連結是否找到未定義的符號。 /FORCE: 如果無法解析進入點符號, 則會忽略無法解析的。

### <a name="create-hot-patchable-image"></a>建立熱可修補映射

準備映射以進行熱修補。

**做**

- [**已啟用**]-準備映射以進行熱修補。
- **僅限 X86 映射**-準備適用于熱修補的 x86 映射。
- **僅 X64 映射**-準備適用于熱修補的 X64 映射。
- **僅限 Itanium 映射**-準備適用于熱修補的 itanium 映射。

### <a name="specify-section-attributes"></a>指定區段屬性

[/SECTION](section-specify-section-attributes.md)選項會變更區段的屬性, 並覆寫在編譯區段的 .obj 檔案時所設定的屬性。

## <a name="input-property-page"></a>輸入屬性頁

### <a name="additional-dependencies"></a>其他相依性

指定要加入至連結命令列的其他專案, 例如*kernel32.dll*。

### <a name="ignore-all-default-libraries"></a>忽略所有預設程式庫

[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)選項會指示連結器在解析外部參考時, 從其搜尋的程式庫清單中移除一或多個預設程式庫。 

### <a name="ignore-specific-default-libraries"></a>忽略特定的預設程式庫

指定要忽略的預設程式庫的一或多個名稱;以分號分隔多個程式庫。 (/NODEFAULTLIB: [名稱, 名稱, ...])

### <a name="module-definition-file"></a>模組定義檔

[/DEF](def-specify-module-definition-file.md)選項會將模組定義檔 (.def) 傳遞至連結器。 只能指定一個 .def 檔來連結。 

### <a name="add-module-to-assembly"></a>將模組新增至元件

[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)選項可讓您將模組參考新增至元件。 模組中的類型資訊將無法供加入模組參考的元件程式使用。 不過, 模組中的型別資訊將可供任何參考元件的程式使用。

### <a name="embed-managed-resource-file"></a>內嵌受控資源檔

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)會將資源檔內嵌在輸出檔案中。

### <a name="force-symbol-references"></a>強制符號參考

[/INCLUDE](include-force-symbol-references.md)選項會告訴連結器將指定的符號加入至符號表。

### <a name="delay-loaded-dlls"></a>延遲載入的 Dll

[/DELAYLOAD](delayload-delay-load-import.md)選項會導致 dll 的延遲載入。 Dll 名稱會指定要延遲載入的 DLL。 

### <a name="assembly-link-resource"></a>元件連結資源

[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)選項會在輸出檔中建立 .NET Framework 資源的連結;資源檔不會放在輸出檔中。

## <a name="manifest-file-property-page"></a>資訊清單檔案屬性頁

### <a name="generate-manifest"></a>產生資訊清單

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)指定連結器應該建立並存資訊清單檔。

### <a name="manifest-file"></a>資訊清單檔

[/MANIFESTFILE](manifestfile-name-manifest-file.md)可讓您變更資訊清單檔的預設名稱。 資訊清單檔的預設名稱是附加 .manifest 的檔案名。

### <a name="additional-manifest-dependencies"></a>其他資訊清單相依性

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)可讓您指定將放入資訊清單檔之相依性區段的屬性。

### <a name="allow-isolation"></a>允許隔離

指定資訊清單查閱的行為。 ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): NO)

### <a name="enable-user-account-control-uac"></a>啟用使用者帳戶控制 (UAC)

指定是否啟用使用者帳戶控制。  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: NO)

### <a name="uac-execution-level"></a>UAC 執行層級

指定以使用者帳戶控制執行時, 應用程式所要求的執行層級。  (/MANIFESTUAC: level = [value])

**做**

- **asInvoker** -UAC 執行層級: 作為啟動端。
- **highestAvailable** -UAC 執行層級: 最高可用。
- **requireAdministrator** -UAC 執行層級: 需要系統管理員。

### <a name="uac-bypass-ui-protection"></a>UAC 略過 UI 保護

指定是否要略過桌面上其他視窗的使用者介面保護層級。  僅針對協助工具應用程式, 將此屬性設定為 [是]。  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): uiAccess = [true | false])

## <a name="debugging-property-page"></a>偵錯屬性頁

### <a name="generate-debug-info"></a>產生調試資訊

此選項可讓您建立 .exe 檔或 DLL 的偵錯工具資訊。

**做**

- **否**-不產生任何調試資訊。
- **產生偵錯工具資訊**-建立適用于散發至 Microsoft 符號伺服器的完整程式資料庫 (PDB)。
- **產生針對更快速連結而優化的 Debug 資訊**-產生適用于編輯-連結-Debug 迴圈的程式資料庫 (PDB)。 
- **產生針對共用和發行優化的調試**程式-產生適用于「編輯-連結-自設計」迴圈的程式資料庫 (PDB)。 

### <a name="generate-program-database-file"></a>產生程式資料庫檔案

根據預設, 當指定[/debug](debug-generate-debug-info.md)時, 連結器會建立程式資料庫 (PDB), 其中包含偵錯工具資訊。 PDB 的預設檔案名具有程式的基底名稱和副檔名 .pdb。

### <a name="strip-private-symbols"></a>去除私用符號

當您使用任何產生 PDB 檔的編譯器或連結器選項 (/DEBUG、/Z7、/Zd 或/Zi) 來建立程式映射時, [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)選項會建立第二個程式資料庫 (PDB) 檔案。

### <a name="generate-map-file"></a>產生對應檔

[/MAP](map-generate-mapfile.md)選項會告訴連結器建立對應檔。

### <a name="map-file-name"></a>對應檔案名稱

使用者指定的對應檔名稱。 它會取代預設名稱。

### <a name="map-exports"></a>對應匯出

[/MAPINFO](mapinfo-include-information-in-mapfile.md)選項會告訴連結器將指定的資訊包含在對應檔中, 如果您指定了/MAP 選項, 就會建立此對應檔。 匯出會告訴連結器包含匯出的函式。

### <a name="debuggable-assembly"></a>能調試元件

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)會發出具有「調試資訊追蹤」的 DebuggableAttribute 屬性, 並停用 JIT 優化。

## <a name="system-property-page"></a>系統屬性頁

### <a name="subsystem"></a>子系統

[/SUBSYSTEM](subsystem-specify-subsystem.md)選項會告訴作業系統如何執行 .exe 檔。子系統的選擇會影響連結器會選擇的進入點符號 (或進入點函式)。

**做**

- **未設定**-未設定子系統。
- **主控台**-Win32 字元模式應用程式。 主控台應用程式是由作業系統提供主控台。 如果已定義 main 或 wmain, 則主控台為預設值。
- **Windows** -應用程式不需要主控台, 可能是因為它會建立自己的視窗來與使用者互動。 如果定義了 WinMain 或 wWinMain, WINDOWS 就是預設值。
- 適用于 Windows NT 的**原生**設備磁碟機。 如果指定了/DRIVER: WDM, 則預設值為 NATIVE。
- **Efi 應用程式**-Efi 應用程式。
- **Efi 開機服務驅動程式**-Efi 開機服務驅動程式。
- **EFI ROM** -EFI ROM。
- **Efi 運行**時間-efi 執行時間。
- **Posix** -在 Windows NT 中使用 posix 子系統執行的應用程式。

### <a name="minimum-required-version"></a>最低必要版本

指定子系統的最小必要版本。 引數是0到65535範圍內的十進位數。

### <a name="heap-reserve-size"></a>堆積保留大小

指定虛擬記憶體中的堆積配置大小總計。 預設值為 1 MB。    ([/HEAP](heap-set-heap-size.md): reserve)

### <a name="heap-commit-size"></a>堆積認可大小

指定實體記憶體中的堆積配置大小總計。 預設值為 4 KB。    ([/HEAP](heap-set-heap-size.md): reserve, commit)

### <a name="stack-reserve-size"></a>堆疊保留大小

指定虛擬記憶體中的堆疊配置大小總和。 預設值為 1 MB。     ([/STACK](stack-stack-allocations.md): reserve)

### <a name="stack-commit-size"></a>堆疊認可大小

指定實體記憶體中的堆疊配置大小總計。 預設值為 4 KB。     ([/STACK](stack-stack-allocations.md): reserve, commit)

### <a name="enable-large-addresses"></a>啟用大型位址

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)選項會告訴連結器, 應用程式可以處理大於 2 gb 的位址。 根據預設, 如果未在連結器行上指定/LARGEADDRESSAWARE, 則會啟用/LARGEADDRESSAWARE: NO。

### <a name="terminal-server"></a>終端伺服器

[/TSAWARE](tsaware-create-terminal-server-aware-application.md)選項會在程式映射的選擇性標頭的 [IMAGE_OPTIONAL_HEADER DllCharacteristics] 欄位中設定旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

### <a name="swap-run-from-cd"></a>從光碟片交換執行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)選項會告訴作業系統先將連結器輸出複製到交換檔, 然後從該處執行映射。 這是 Windows NT 4.0 (和更新版本) 的功能。 當指定**CD**時, 作業系統會將卸載式磁片上的映射複製到分頁檔, 然後將它載入。

### <a name="swap-run-from-network"></a>從網路交換執行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)選項會告訴作業系統先將連結器輸出複製到交換檔, 然後從該處執行映射。 這是 Windows NT 4.0 (和更新版本) 的功能。 如果指定**NET** , 作業系統會先將二進位映射從網路複製到交換檔, 然後從該處載入。 此選項適用于透過網路執行應用程式。

### <a name="driver"></a>驅動器

使用[/DRIVER](driver-windows-nt-kernel-mode-driver.md)連結器選項來建立 Windows NT 核心模式驅動程式。

**做**

- **未設定**-預設驅動程式設定。
- **驅動**程式驅動程式
- **僅限**/DRIVER: UPONLY 會使連結器將 IMAGE_FILE_UP_SYSTEM_ONLY 位新增至輸出標頭中的特性, 以指定它是單處理器 (UP) 驅動程式。 作業系統會拒絕在多處理器 (MP) 系統上載入驅動程式。
- **Wdm** -/DRIVER: wdm 會使連結器在選擇性標頭的 DLLCHARACTERISTICS 欄位中設定 IMAGE_DLLCHARACTERISTICS_WDM_DRIVER 位。

## <a name="optimization-property-page"></a>優化屬性頁

### <a name="references"></a>參考

[/Opt](opt-optimizations.md): REF 會排除未參考的函式和 (或) 資料, 而/OPT: NOREF 會保留從未參考的函式和 (或) 資料。 

### <a name="enable-comdat-folding"></a>啟用 COMDAT 摺疊

使用[/opt](opt-optimizations.md): ICF\[= 反復專案] 來執行相同的 COMDAT 折迭。 

### <a name="function-order"></a>函數順序

[/Order](order-put-functions-in-order.md)選項會告訴連結, 藉由以預先決定的順序將特定 comdat 放入映射中, 將您的程式優化。 連結會依指定的順序, 將函式放在影像中的每個區段內。

### <a name="profile-guided-database"></a>特性指引資料庫

指定適用于特性指引優化的 .pgd 檔案。 ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>連結時間程式碼產生

指定連結時產生程式碼。 ([/LTCG](ltcg-link-time-code-generation.md))

**做**

- **預設**值-預設 LTCG 設定。
- **使用快速連結時間程式碼產生**-搭配[/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)使用連結時間代碼產生。
- **使用連結時間產生程式碼**-使用[連結時間代碼產生](ltcg-link-time-code-generation.md)。
- 特性**指引優化-檢測**-使用特性[指引優化](../profile-guided-optimizations.md)與:P ginstrument。
- 特性**指引優化-優化**-指定連結器應該使用在執行已檢測的二進位檔之後所建立的設定檔資料, 以建立優化的映射。
- 特性**指引優化-更新**-允許和追蹤要從:P ginstrument 階段所指定內容中新增或修改的輸入檔清單。

## <a name="embedded-idl-property-page"></a>內嵌的 IDL 屬性頁

### <a name="midl-commands"></a>MIDL 命令

指定 MIDL 命令列選項。 ([/MIDL](midl-specify-midl-command-line-options.md) :@responsefile)

### <a name="ignore-embedded-idl"></a>忽略內嵌的 IDL

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)選項指定不應將原始程式碼中的任何 IDL 屬性處理成 .idl 檔案。

### <a name="merged-idl-base-file-name"></a>合併的 IDL 基底檔案名

[/IDLOUT](idlout-name-midl-output-files.md)選項會指定 .idl 檔案的名稱和副檔名。

### <a name="type-library"></a>類型程式庫

[/TLBOUT](tlbout-name-dot-tlb-file.md)選項指定 .tlb 檔案的名稱和副檔名。

### <a name="typelib-resource-id"></a>TypeLib 資源識別碼

可讓您指定連結器產生之型別程式庫的資源識別碼。 ([/TLBID](tlbid-specify-resource-id-for-typelib.md): id)

## <a name="windows-metadata-property-page"></a>Windows 中繼資料屬性頁

### <a name="generate-windows-metadata"></a>產生 Windows 中繼資料

啟用或停用 Windows 中繼資料的產生。

**做**

- **是**-啟用產生 Windows 中繼資料檔案。
- **否**-停用產生 Windows 中繼資料檔案。

### <a name="windows-metadata-file"></a>Windows 中繼資料檔案

[/WINMDFILE](winmdfile-specify-winmd-file.md)選項參數。

### <a name="windows-metadata-key-file"></a>Windows 中繼資料金鑰檔

指定用來簽署 Windows 中繼資料的金鑰或金鑰組。 ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): filename)

### <a name="windows-metadata-key-container"></a>Windows 中繼資料金鑰容器

指定用來簽署 Windows 中繼資料的金鑰容器。 ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): name)

### <a name="windows-metadata-delay-sign"></a>Windows 中繼資料延遲簽章

部分簽署 Windows 中繼資料。 如果您只想要將公開金鑰放在 Windows 中繼資料中, 請使用[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) 。 預設值為/WINMDDELAYSIGN: NO。

## <a name="advanced-property-page"></a>Advanced 屬性頁

### <a name="entry-point"></a>進入點

[/ENTRY](entry-entry-point-symbol.md)選項會將進入點函式指定為 .exe 檔或 DLL 的起始位址。

### <a name="no-entry-point"></a>無進入點

建立僅含資源的 DLL 時, 需要[/NOENTRY](noentry-no-entry-point.md)選項。使用此選項可防止連結將參考`_main`連結到 DLL。

### <a name="set-checksum"></a>設定總和檢查碼

[/RELEASE](release-set-the-checksum.md)選項會在 .exe 檔的標頭中設定總和檢查碼。

### <a name="base-address"></a>基底位址

設定程式的基底位址。 ([/Base](base-base-address.md): {address\[, size] |@filename, key})

### <a name="randomized-base-address"></a>隨機基底位址

隨機基底位址。 ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) \[: NO])

### <a name="fixed-base-address"></a>固定基底位址

建立僅可在其慣用基底位址載入的程式。 ([/FIXED](fixed-fixed-base-address.md) \[: NO])

### <a name="data-execution-prevention-dep"></a>資料執行防止 (DEP)

將可執行檔標記為已測試, 以與 Windows 資料執行防止功能相容。 ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md) \[: NO])

### <a name="turn-off-assembly-generation"></a>關閉元件產生

[/NOASSEMBLY](noassembly-create-a-msil-module.md)選項會告訴連結器為目前的輸出檔建立影像, 而不 .NET Framework 元件。

### <a name="unload-delay-loaded-dll"></a>卸載延遲載入的 DLL

**UNLOAD**辨識符號會指示延遲載入 helper 函式支援 DLL 的明確卸載。 ([/DELAY](delay-delay-load-import-settings.md): UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Nobind 延遲載入的 DLL

**NOBIND**限定詞會指示連結器不要在最終映射中包含可系結的 IAT。 預設會是針對延遲載入 DLL 建立可繫結 IAT。 ([/DELAY](delay-delay-load-import-settings.md): NOBIND)

### <a name="import-library"></a>匯入程式庫

覆寫預設匯入程式庫名稱。 ([/IMPLIB](implib-name-import-library.md): filename)

### <a name="merge-sections"></a>合併區段

[/Merge](merge-combine-sections.md)選項會將第一個區段 (來自) 與第二個區段 (至) 結合, 並將產生的區段命名為。 例如,/merge:. .rdata =. text。

### <a name="target-machine"></a>目的電腦

[/MACHINE](machine-specify-target-platform.md)選項會指定程式的目標平臺。

**做**

- **未設定**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>設定檔

產生可與效能工具分析工具搭配使用的輸出檔。 需要設定 GenerateDebugInformation (/[/debug](debug-generate-debug-info.md))。 ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR 執行緒屬性

明確指定 CLR 程式進入點的執行緒屬性。

**做**

- **MTA 執行緒屬性**-將 MTAThreadAttribute 屬性套用至程式的進入點。
- **STA 執行緒屬性**-將 STAThreadAttribute 屬性套用至程式的進入點。
- **預設的執行緒屬性**-與未指定[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)相同。 讓 Common Language Runtime (CLR) 設定預設的執行緒屬性。

### <a name="clr-image-type"></a>CLR 映射類型

設定 CLR 映像的類型 (IJW、純或安全)。

**做**

- **強制 IJW 映射**
- **強制純 IL 映射**
- **強制執行安全 IL 映射**
- **預設映射類型**

### <a name="key-file"></a>金鑰檔

指定用來簽署元件的金鑰或金鑰組。 ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): filename)

### <a name="key-container"></a>金鑰容器

指定要簽署元件的金鑰容器。 ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md): name)

### <a name="delay-sign"></a>延遲簽章

部分簽署元件。 如果您只想要將公開金鑰放在元件中, 請使用[/DELAYSIGN](delaysign-partially-sign-an-assembly.md) 。 預設值為/DELAYSIGN: NO。

### <a name="clr-unmanaged-code-check"></a>CLR 非受控碼檢查

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)指定連結器是否會將 SuppressUnmanagedCodeSecurityAttribute 套用至連結器產生的 PInvoke 呼叫, 從 managed 程式碼到原生 dll。

### <a name="error-reporting"></a>錯誤報表

讓您直接提供內部編譯器錯誤 (ICE) 資訊給 Visual C++ 團隊。

**做**

- **PromptImmediately** -立即提示。
- 下一個登入佇列的**佇列**, 用於下一個登入。
- **傳送錯誤報表**-傳送錯誤報表。
- **沒有錯誤報表**-沒有錯誤報表。

### <a name="sectionalignment"></a>SectionAlignment

[/Align](align-section-alignment.md)選項會指定程式之線性位址空間內每個區段的對齊方式。 Number 引數是以位元組為單位, 而且必須是2的乘冪。

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>保留 PInvoke 呼叫的最後一個錯誤碼

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)(預設為開啟) 會保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼, 這可讓您從使用/clr 編譯的程式碼中, 呼叫 dll 中的原生函式

**做**

- [**已啟用**]-啟用 CLRSupportLastError。
- **Disabled** -停用 CLRSupportLastError。
- **僅限系統 dll** -僅針對系統 Dll 啟用 CLRSupportLastError。

### <a name="image-has-safe-exception-handlers"></a>影像具有安全的例外狀況處理常式

當您指定[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)時, 如果連結器也可以產生影像的安全例外狀況處理常式的資料表, 則它只會產生影像。 此資料表會為作業系統指定哪些例外狀況處理常式對映射有效。
