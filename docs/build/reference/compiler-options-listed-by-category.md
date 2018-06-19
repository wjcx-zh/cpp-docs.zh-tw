---
title: 依分類排列的編譯器選項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fff661bf573ca30a5b0e7550c2e53b00a7ff3d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379324"
---
# <a name="compiler-options-listed-by-category"></a>依分類排列的編譯器選項

本文包含編譯器選項的分類清單。 如需依字母順序排列的清單，請參閱[編譯器選項依字母順序列出](compiler-options-listed-alphabetically.md)。

### <a name="optimization"></a>最佳化

|選項|用途|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|建立小型程式碼。|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|建立快速程式碼。|
|[/Ob](ob-inline-function-expansion.md)|控制內嵌展開。|
|[/Od](od-disable-debug.md)|停用最佳化。|
|[/Og](og-global-optimizations.md)|已取代。 使用全域最佳化。|
|[/Oi](oi-generate-intrinsic-functions.md)|產生內建函式。|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|偏好小的程式碼。|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|偏好快的程式碼。|
|[/Ox](ox-full-optimization.md)|使用最大最佳化 (/Ob2gity /Gs)。|
|[/Oy](oy-frame-pointer-omission.md)|省略框架指標。 (僅限 x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|產生針對指定之結構或結構範圍進行最佳化的程式碼。|

### <a name="code-generation"></a>程式碼產生

|選項|用途|
|------------|-------------|
|[/arch](arch-x86.md)|在程式碼產生時使用 SSE 或 SSE2 指令。 (僅限 x86)|
|[/clr](clr-common-language-runtime-compilation.md)|產生輸出檔案，以便在 Common Language Runtime 上執行。|
|[/EH](eh-exception-handling-model.md)|指定例外狀況處理模型。|
|[/fp](fp-specify-floating-point-behavior.md)|指定浮點行為。|
|[/GA](ga-optimize-for-windows-application.md)|對 Windows 應用程式進行最佳化。|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|使用 `__cdecl` 呼叫慣例。 (僅限 x86)|
|[/Ge](ge-enable-stack-probes.md)|已取代。 啟動堆疊探查。|
|[/GF](gf-eliminate-duplicate-strings.md)|啟用字串共用。|
|[/Gh](gh-enable-penter-hook-function.md)|呼叫攔截函式 `_penter`。|
|[/GH](gh-enable-pexit-hook-function.md)|呼叫攔截函式 `_pexit`。|
|[/GL](gl-whole-program-optimization.md)|啟用整個程式最佳化。|
|[/Gm](gm-enable-minimal-rebuild.md)|啟用最少重建。|
|[/GR](gr-enable-run-time-type-information.md)|啟用執行階段類型資訊 (RTTI)。|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|使用 `__fastcall` 呼叫慣例。 (僅限 x86)|
|[/GS](gs-buffer-security-check.md)|檢查緩衝區安全性。|
|[/Gs](gs-control-stack-checking-calls.md)|控制堆疊探查。|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|對使用靜態執行緒區域儲存區所配置的資料支援 Fiber 安全性。|
|[/guard:cf](guard-enable-control-flow-guard.md)|加入控制流程防護安全性檢查。|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|使用 `__vectorcall` 呼叫慣例。 (僅限 x86 和 x64)|
|[/Gw](gw-optimize-global-data.md)|啟用整個程式全域資料最佳化。|
|[/GX](gx-enable-exception-handling.md)|已取代。 啟用同步例外狀況處理。 使用[/EH](eh-exception-handling-model.md)改為。|
|[/Gy](gy-enable-function-level-linking.md)|啟用函式階層連結。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|已取代。 啟用快速檢查。 (與相同[/RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|使用 `__stdcall` 呼叫慣例。 (僅限 x86)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|在函式進入時，強制暫存器中所傳遞的參數寫入至堆疊上的位置。 這個編譯器選項只適用於 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯器 (原生和跨平台編譯)。|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|建立可線上修補的影像。|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|產生快速超越函式。|
|[/Qifist](qifist-suppress-ftol.md)|已取代。 在必須從浮點類型轉換為整數類型時，抑制對 Helper 函式 `_ftol` 的呼叫。 (僅限 x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|移除 `fwait` 區塊內的 `try` 命令。|
|[/Qpar](qpar-auto-parallelizer.md)|啟用迴圈自動平行處理。|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|啟用自動平行處理的報告層級。|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|使用浮點值的整數移動指令，並停用特定浮點數負載最佳化。|
|[/Qspectre](qspectre.md)|啟用 CVE 2017 5753，類別 Spectre 攻擊的防護功能。|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|啟用自動向量化的報告層級。|
|[/RTC](rtc-run-time-error-checks.md)|啟用執行階段錯誤檢查。|
|[/volatile](volatile-volatile-keyword-interpretation.md)|選取 volatile 關鍵字的解譯方式。|

### <a name="output-files"></a>輸出檔

|選項|用途|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|將文件註解處理成 XML 檔案。|
|[/FA](fa-fa-listing-file.md)|設定組件清單檔。|
|[/Fa](fa-fa-listing-file.md)|建立組件清單檔。|
|[/Fd](fd-program-database-file-name.md)|重新命名程式資料庫檔案。|
|[/Fe](fe-name-exe-file.md)|重新命名可執行檔。|
|[/Fi](fi-preprocess-output-file-name.md)|指定前置處理過的輸出檔名稱。|
|[/Fm](fm-name-mapfile.md)|建立對應檔 (Mapfile)。|
|[/Fo](fo-object-file-name.md)|建立目的檔。|
|[/Fp](fp-name-dot-pch-file.md)|指定先行編譯標頭檔的名稱。|
|[/FR, /Fr](fr-fr-create-dot-sbr-file.md)|產生瀏覽器的.sbr 檔案名稱。|

### <a name="preprocessor"></a>前置處理器

|選項|用途|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|指定一個要搜尋的目錄，以解析傳遞給 [#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞的檔案參考。|
|[/C](c-preserve-comments-during-preprocessing.md)|在前置處理過程中保留註解。|
|[/D](d-preprocessor-definitions.md)|定義常數和巨集。|
|[/E](e-preprocess-to-stdout.md)|複製前置處理器輸出至標準輸出。|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|複製前置處理器輸出至標準輸出。|
|[/FI](fi-name-forced-include-file.md)|前置處理指定的包含檔。|
|[/FU](fu-name-forced-hash-using-file.md)|強制使用某個檔案名稱，就如同其已傳遞給 [#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞一般。|
|[/Fx](fx-merge-injected-code.md)|將插入的程式碼與原始程式檔合併。|
|[/I](i-additional-include-directories.md)|搜尋包含檔的目錄。|
|[/P](p-preprocess-to-a-file.md)|將前置處理器輸出寫入檔案。|
|[/U](u-u-undefine-symbols.md)|移除某個預先定義巨集。|
|[/u](u-u-undefine-symbols.md)|移除所有預先定義巨集。|
|[/X](x-ignore-standard-include-paths.md)|忽略標準 Include 目錄。|

### <a name="language"></a>語言

|選項|用途|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|控制在編譯時期的 constexpr 評估。|
|[/openmp](openmp-enable-openmp-2-0-support.md)|在原始程式碼中啟用 [#pragma omp](../../preprocessor/omp.md) 。|
|[/vd](vd-disable-construction-displacements.md)|抑制或啟用隱藏的 `vtordisp` 類別成員。|
|[/vmb](vmb-vmg-representation-method.md)|對指向成員的指標使用最佳基底。|
|[/vmg](vmb-vmg-representation-method.md)|對指向成員的指標使用完整一般性。|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|宣告多重繼承。|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|宣告單一繼承。|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|宣告虛擬繼承。|
|[/Z7](z7-zi-zi-debug-information-format.md)|產生 C 7.0 相容的偵錯資訊。|
|[/Za](za-ze-disable-language-extensions.md)|停用語言擴充功能。|
|[/Zc](zc-conformance.md)|指定下的標準行為[/Ze](za-ze-disable-language-extensions.md)。|
|[/Ze](za-ze-disable-language-extensions.md)|已取代。 啟用語言擴充功能。|
|[/Zf](zf.md)|改善 PDB 平行組建中產生時間。|
|[/ZI](z7-zi-zi-debug-information-format.md)|將偵錯資訊包括在與「編輯後繼續」相容的程式資料庫中。 (僅限 x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|產生完整偵錯資訊。|
|[/Zl](zl-omit-default-library-name.md)|從 .obj 檔案移除預設程式庫名稱。|
|[/Zp](zp-struct-member-alignment.md) *n*|封裝結構成員。|
|[/Zs](zs-syntax-check-only.md)|僅檢查語法。|
|[/ZW](zw-windows-runtime-compilation.md)|產生輸出檔案，以便在 Windows 執行階段上執行。|

### <a name="linking"></a>連結

|選項|用途|
|------------|-------------|
|[/F](f-set-stack-size.md)|設定堆疊大小。|
|[/LD](md-mt-ld-use-run-time-library.md)|建立動態連結程式庫。|
|[/LDd](md-mt-ld-use-run-time-library.md)|建立偵錯動態連結程式庫。|
|[/link](link-pass-options-to-linker.md)|傳遞指定的選項給 LINK。|
|[/LN](ln-create-msil-module.md)|建立 MSIL 模組。|
|[/MD](md-mt-ld-use-run-time-library.md)|使用 MSVCRT.lib 編譯以建立多執行緒 DLL。|
|[/MDd](md-mt-ld-use-run-time-library.md)|使用 MSVCRTD.lib 編譯以建立偵錯多執行緒 DLL。|
|[/MT](md-mt-ld-use-run-time-library.md)|使用 LIBCMT.lib 編譯以建立多執行緒可執行檔。|
|[/MTd](md-mt-ld-use-run-time-library.md)|使用 LIBCMTD.lib 編譯以建立偵錯多執行緒可執行檔。|

### <a name="miscellaneous"></a>其他

|選項|用途|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|列出編譯器選項。|
|[@](at-specify-a-compiler-response-file.md)|指定回應檔。|
|[分析 /](analyze-code-analysis.md)|啟用程式碼分析。|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|增加 .obj 檔案中可定址區段的數目。|
|[/c](c-compile-without-linking.md)|編譯而不連結。|
|[/cgthreads](cgthreads-code-generation-threads.md)|指定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|可讓您直接提供內部編譯器錯誤 (ICE) 資訊給 Visual C++ 團隊。|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|在診斷文字中顯示傳遞給 cl.exe 的原始程式檔完整路徑。|
|[/FS](fs-force-synchronous-pdb-writes.md)|強制寫入要透過 MSPDBSRV.EXE 序列化的程式資料庫 (PDB) 檔案。|
|[/H](h-restrict-length-of-external-names.md)|已取代。 限制外部 (公用) 名稱的長度。|
|[/HELP](help-compiler-command-line-help.md)|列出編譯器選項。|
|[/J](j-default-char-type-is-unsigned.md)|變更預設 `char` 類型。|
|[/kernel](kernel-create-kernel-mode-binary.md)|編譯器和連結器將會建立可以在 Windows 核心中執行的二進位檔。|
|[/MP](mp-build-with-multiple-processes.md)|同時建置多重原始程式檔。|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|隱藏登入程式的啟始資訊。|
|[/sdl](sdl-enable-additional-security-checks.md)|啟用其他安全性功能及警告。|
|[/showIncludes](showincludes-list-include-files.md)|在編譯時顯示所有 Include 檔的清單。|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|指定 C 原始程式檔。|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|指定所有的來源檔案的 c。|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|指定 C++ 原始程式檔。|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|指定所有原始程式檔的 c + +。|
|[/V](v-version-number.md)|已取代。 設定版本字串。|
|[/w](compiler-option-warning-level.md)|停用所有警告。|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|設定輸出警告層級。|
|[/w1、 /w2、 /w3、 /w4](compiler-option-warning-level.md)|為指定的警告設定警告層級。|
|[/Wall](compiler-option-warning-level.md)|啟用所有警告，包括預設停用的警告。|
|[/wd](compiler-option-warning-level.md)|停用指定的警告。|
|[/we](compiler-option-warning-level.md)|將指定的警告視為錯誤。|
|[/WL](wl-enable-one-line-diagnostics.md)|從命令列編譯 C++ 原始程式碼時啟用一行錯誤和警告訊息診斷。|
|[/wo](compiler-option-warning-level.md)|只顯示指定的警告一次。|
|[/Wv](compiler-option-warning-level.md)|停用較新版編譯器所引入的警告。|
|[/WX](compiler-option-warning-level.md)|將警告視為錯誤。|
|[/Yc](yc-create-precompiled-header-file.md)|建立。PCH 檔案。|
|[/Yd](yd-place-debug-information-in-object-file.md)|已取代。 將完整的偵錯資訊置於所有目的檔中。 使用[/Zi](z7-zi-zi-debug-information-format.md)改為。|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|在建立偵錯程式庫時插入 PCH 參考。|
|[/Yu](yu-use-precompiled-header-file.md)|在建置時使用先行編譯標頭檔。|
|[/Y-](y-ignore-precompiled-header-options.md)|忽略目前組建中所有其他先行編譯標頭編譯器選項。|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|指定先行編譯標頭的記憶體配置上限。|
|[/await](await-enable-coroutine-support.md)|啟用協同程式 （可繼續函式） 擴充功能。|
|[/source-charset](source-charset-set-source-character-set.md)|設定來源字元集。|
|[/execution-charset](execution-charset-set-execution-character-set.md)|設定執行字元集。|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|設定來源和執行字元集為 utf-8。|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|確認只有相容的字元的 utf-8 檔案。|
|[/diagnostics](diagnostics-compiler-diagnostic-options.md)|控制診斷訊息的格式。|
|[/permissive-](permissive-standards-conformance.md)|設定標準一致性模式。|
|[/std](std-specify-language-standard-version.md)|C + + 標準版本相容性的選取器。|

### <a name="deprecated-and-removed-compiler-options"></a>已取代及移除編譯器選項

|選項|用途|
|------------|-------------|
|[/clr:noAssembly](clr-common-language-runtime-compilation.md)|已取代。 使用[/LN （建立 MSIL 模組）](ln-create-msil-module.md)改為。|
|[/Fr](fr-fr-create-dot-sbr-file.md)|已取代。 建立不包含本機變數的瀏覽資訊檔。|
|[/Ge](ge-enable-stack-probes.md)|已取代。 啟動堆疊探查。 預設為開啟。|
|[/GX](gx-enable-exception-handling.md)|已取代。 啟用同步例外狀況處理。 使用[/EH](eh-exception-handling-model.md)改為。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|已取代。 啟用快速檢查。 使用[/RTC1](rtc-run-time-error-checks.md)改為。|
|[/H](h-restrict-length-of-external-names.md)|已取代。 限制外部 (公用) 名稱的長度。|
|[/Og](og-global-optimizations.md)|已取代。 使用全域最佳化。|
|[/Qifist](qifist-suppress-ftol.md)|已取代。 曾用以指定如何從浮點型別轉換為整數型別。|
|[/V](v-version-number.md)|已取代。 設定 obj 檔案版本字串。|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|已過時。 偵測 64 位元可移植性問題。|
|[/Yd](yd-place-debug-information-in-object-file.md)|已取代。 將完整的偵錯資訊置於所有目的檔中。 使用[/Zi](z7-zi-zi-debug-information-format.md)改為。|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|已取代。 停用 For 迴圈範圍中的一致性。|
|[/Ze](za-ze-disable-language-extensions.md)|已取代。 啟用語言擴充功能。|
|[/Zg](zg-generate-function-prototypes.md)|已從 Visual C++ 2015 移除。 產生函式原型。|

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)<br/>
[編譯器選項](compiler-options.md)<br/>
[設定編譯器選項](setting-compiler-options.md)<br/>
