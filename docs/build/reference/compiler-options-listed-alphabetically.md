---
title: 依字母順序排列的編譯器選項
ms.date: 08/20/2018
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: fa5ae089e112c147fb5e18b13af2ef5b95a7fda3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646728"
---
# <a name="compiler-options-listed-alphabetically"></a>依字母順序排列的編譯器選項

以下是編譯器選項的完整字母順序清單。 如需分類清單，請參閱 [依分類排列的編譯器選項](compiler-options-listed-by-category.md)。

|選項|用途|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|指定回應檔。|
|[/?](help-compiler-command-line-help.md)|列出編譯器選項。|
|[/AI](ai-specify-metadata-directories.md)|指定一個要搜尋的目錄，以解析傳遞給 [#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞的檔案參考。|
|[/analyze](analyze-code-analysis.md)|啟用程式碼分析|
|[/arch](arch-minimum-cpu-architecture.md)|為程式碼產生指定架構。|
|[/ await](await-enable-coroutine-support.md)|啟用協同程式 （可繼續函式） 擴充功能。|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|增加 .obj 檔案中可定址區段的數目。|
|[/C](c-preserve-comments-during-preprocessing.md)|在前置處理過程中保留註解。|
|[/c](c-compile-without-linking.md)|編譯而不連結。|
|[/cgthreads](cgthreads-code-generation-threads.md)|指定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。|
|[/clr](clr-common-language-runtime-compilation.md)|產生輸出檔案，以便在 Common Language Runtime 上執行。|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|在編譯時期的控制 constexpr 評估。|
|[/D](d-preprocessor-definitions.md)|定義常數和巨集。|
|[/diagnostics](diagnostics-compiler-diagnostic-options.md)|控制診斷訊息的格式。|
|[/doc](doc-process-documentation-comments-c-cpp.md)|將文件註解處理成 XML 檔案。|
|[/E](e-preprocess-to-stdout.md)|複製前置處理器輸出至標準輸出。|
|[/EH](eh-exception-handling-model.md)|指定例外狀況處理模型。|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|複製前置處理器輸出至標準輸出。|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|讓您直接提供內部編譯器錯誤 (ICE) 資訊給 Visual C++ 團隊。|
|[/execution-charset](execution-charset-set-execution-character-set.md)|設定執行字元集。|
|[/F](f-set-stack-size.md)|設定堆疊大小。|
|[/favor](favor-optimize-for-architecture-specifics.md)|產生程式碼，適用於特定的 x64 架構或為 AMD64 和延伸記憶體 64 技術 (EM64T) 架構中微-架構。|
|[/FA](fa-fa-listing-file.md)|建立清單檔。|
|[/Fa](fa-fa-listing-file.md)|設定清單檔名稱。|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|顯示在診斷測試中傳遞給 cl.exe 的原始程式檔完整路徑。|
|[/Fd](fd-program-database-file-name.md)|重新命名程式資料庫檔案。|
|[/Fe](fe-name-exe-file.md)|重新命名可執行檔。|
|[/FI](fi-name-forced-include-file.md)|前置處理指定的包含檔。|
|[/Fi](fi-preprocess-output-file-name.md)|設定前置處理過的輸出檔名稱。|
|[/Fm](fm-name-mapfile.md)|建立對應檔 (Mapfile)。|
|[/Fo](fo-object-file-name.md)|建立目的檔。|
|[/fp](fp-specify-floating-point-behavior.md)|指定浮點行為。|
|[/Fp](fp-name-dot-pch-file.md)|指定先行編譯標頭檔的名稱。|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/Fr](fr-fr-create-dot-sbr-file.md)|產生瀏覽器檔案。 **/Fr** 已取代。|
|[/FS](fs-force-synchronous-pdb-writes.md)|強制寫入要透過 MSPDBSRV.EXE 序列化的程式資料庫 (PDB) 檔案。|
|[/FU](fu-name-forced-hash-using-file.md)|強制使用某一檔名，就如同它已傳遞給 [#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞一樣。|
|[/Fx](fx-merge-injected-code.md)|將插入的程式碼與原始程式檔合併。|
|[/GA](ga-optimize-for-windows-application.md)|對 Windows 應用程式進行程式碼最佳化。|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|使用 `__cdecl` 呼叫慣例 (僅適用於 x86)。|
|[/Ge](ge-enable-stack-probes.md)|已取代。 啟動堆疊探查。|
|[/GF](gf-eliminate-duplicate-strings.md)|啟用字串共用。|
|[/GH](gh-enable-pexit-hook-function.md)|呼叫攔截函式 `_pexit`。|
|[/Gh](gh-enable-penter-hook-function.md)|呼叫攔截函式 `_penter`。|
|[/GL](gl-whole-program-optimization.md)|啟用整個程式最佳化。|
|[/Gm](gm-enable-minimal-rebuild.md)|啟用最少重建。|
|[/GR](gr-enable-run-time-type-information.md)|啟用執行階段類型資訊 (RTTI)。|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|使用 `__fastcall` 呼叫慣例 (僅適用於 x86)。|
|[/GS](gs-buffer-security-check.md)|緩衝處理安全性檢查。|
|[/Gs](gs-control-stack-checking-calls.md)|控制堆疊探查。|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|對使用靜態執行緒區域儲存區配置的資料支援 Fiber 安全性。|
|[/guard:cf](guard-enable-control-flow-guard.md)|加入控制流程防護安全性檢查。|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|使用 `__vectorcall` 呼叫慣例。 (僅限 x86 和 x64)|
|[/Gw](gw-optimize-global-data.md)|啟用整個程式全域資料最佳化。|
|[/GX](gx-enable-exception-handling.md)|已取代。 啟用同步例外狀況處理。 改用 [/EH](eh-exception-handling-model.md) 。|
|[/Gy](gy-enable-function-level-linking.md)|啟用函式階層連結。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|已取代。 與 [/RTC1](rtc-run-time-error-checks.md)相同。|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|使用 `__stdcall` 呼叫慣例 (僅適用於 x86)。|
|[/H](h-restrict-length-of-external-names.md)|已取代。 限制外部 (公用) 名稱的長度。|
|[/HELP](help-compiler-command-line-help.md)|列出編譯器選項。|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|在函式進入時，強制暫存器中所傳遞的參數寫入至堆疊上的位置。 這個編譯器選項是僅適用於 x64 編譯器 （原生和跨編譯）。|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|建立可線上修補的影像。|
|[/I](i-additional-include-directories.md)|搜尋包含檔的目錄。|
|[/J](j-default-char-type-is-unsigned.md)|變更預設 `char` 類型。|
|[/ JMC](jmc.md)|支援原生 c + + Just My Code 偵錯。|
|[/kernel](kernel-create-kernel-mode-binary.md)|編譯器和連結器將會建立可以在 Windows 核心中執行的二進位檔。|
|[/LD](md-mt-ld-use-run-time-library.md)|建立動態連結程式庫。|
|[/LDd](md-mt-ld-use-run-time-library.md)|建立偵錯動態連結程式庫。|
|[/link](link-pass-options-to-linker.md)|傳遞指定的選項給 LINK。|
|[/LN](ln-create-msil-module.md)|建立 MSIL 模組。|
|[/MD](md-mt-ld-use-run-time-library.md)|使用 MSVCRT.lib 建立多執行緒 DLL。|
|[/MDd](md-mt-ld-use-run-time-library.md)|使用 MSVCRTD.lib 建立偵錯多執行緒 DLL。|
|[/MP](mp-build-with-multiple-processes.md)|使用多重處理序編譯多重原始程式檔。|
|[/MT](md-mt-ld-use-run-time-library.md)|使用 LIBCMT.lib 建立多執行緒可執行檔。|
|[/MTd](md-mt-ld-use-run-time-library.md)|使用 LIBCMTD.lib 建立偵錯多執行緒可執行檔。|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|隱藏登入程式的啟始資訊。|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|建立小型程式碼。|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|建立快速程式碼。|
|[/Ob](ob-inline-function-expansion.md)|控制內嵌展開。|
|[/Od](od-disable-debug.md)|停用最佳化。|
|[/Og](og-global-optimizations.md)|已取代。 使用全域最佳化。|
|[/Oi](oi-generate-intrinsic-functions.md)|產生內建函式。|
|[/openmp](openmp-enable-openmp-2-0-support.md)|在原始程式碼中啟用 [#pragma omp](../../preprocessor/omp.md) 。|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|偏好小的程式碼。|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|偏好快的程式碼。|
|[/Ox](ox-full-optimization.md)|使用最大最佳化 (/Ob2gity /Gs)。|
|[/Oy](oy-frame-pointer-omission.md)|省略框架指標 (僅適用於 x86)。|
|[/P](p-preprocess-to-a-file.md)|將前置處理器輸出寫入檔案。|
|[/permissive-](permissive-standards-conformance.md)|設定標準一致性模式。|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|產生快速超越函式。|
|[/QIfist](qifist-suppress-ftol.md)|已取代。 在必須從浮點類型轉換為整數類型時，抑制 `_ftol` (僅適用於 x86)。|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|移除 `fwait` 區塊內的 `try` 命令。|
|[/Qpar (自動平行化工具)](qpar-auto-parallelizer.md)|啟用標記為 [#pragma loop()](../../preprocessor/loop.md) 指示詞之迴圈的自動平行處理。|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|使用浮點值的整數移動指令，並停用特定浮點數負載最佳化。|
|[/Qvec-report (自動向量化工具報告層級)](qvec-report-auto-vectorizer-reporting-level.md)|啟用自動向量化的報告層級。|
|[/RTC](rtc-run-time-error-checks.md)|啟用執行階段錯誤檢查。|
|[/sdl](sdl-enable-additional-security-checks.md)|啟用其他安全性功能及警告。|
|[/showIncludes](showincludes-list-include-files.md)|在編譯時顯示包含檔清單。|
|[/source-charset](source-charset-set-source-character-set.md)|設定來源字元集。|
|[/std](std-specify-language-standard-version.md)|C + + 標準的版本相容性的選取器。|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|指定 C 原始程式檔。|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|指定所有原始程式檔都是 c。|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|指定 C++ 原始程式檔。|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|指定所有原始程式檔的 c + +。|
|[/U](u-u-undefine-symbols.md)|移除某個預先定義巨集。|
|[/u](u-u-undefine-symbols.md)|移除所有預先定義巨集。|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|設定來源和執行字元集為 utf-8。|
|[/V](v-version-number.md)|已取代。 設定 obj 檔案版本字串。|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|驗證只有相容字元的 utf-8 檔案。|
|[/vd](vd-disable-construction-displacements.md)|抑制或啟用隱藏的 vtordisp 類別成員。|
|[/vmb](vmb-vmg-representation-method.md)|對指向成員的指標使用最佳基底。|
|[/vmg](vmb-vmg-representation-method.md)|對指向成員的指標使用完整一般性。|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|宣告多重繼承。|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|宣告單一繼承。|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|宣告虛擬繼承。|
|[/volatile](volatile-volatile-keyword-interpretation.md)|選取 volatile 關鍵字的解譯方式。|
|[/w](compiler-option-warning-level.md)|停用所有警告。|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|設定要輸出的警告層級。|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|為指定的警告設定警告層級。|
|[/Wall](compiler-option-warning-level.md)|啟用所有警告，包括預設停用的警告。|
|[/wd](compiler-option-warning-level.md)|停用指定的警告。|
|[/we](compiler-option-warning-level.md)|將指定的警告視為錯誤。|
|[/WL](wl-enable-one-line-diagnostics.md)|從命令列編譯 C++ 原始程式碼時啟用一行錯誤和警告訊息診斷。|
|[/wo](compiler-option-warning-level.md)|只顯示指定的警告一次。|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|已過時。 偵測 64 位元可移植性問題。|
|[/Wv](compiler-option-warning-level.md)|在指定的編譯器版本之後顯示未引入任何警告。|
|[/WX](compiler-option-warning-level.md)|將所有警告視為錯誤。|
|[/X](x-ignore-standard-include-paths.md)|忽略標準 Include 目錄。|
|[/Y-](y-ignore-precompiled-header-options.md)|忽略目前組建中所有其他先行編譯標頭編譯器選項。|
|[/Yc](yc-create-precompiled-header-file.md)|建立先行編譯標頭檔。|
|[/Yd](yd-place-debug-information-in-object-file.md)|已取代。 將完整的偵錯資訊置於所有目的檔中。 改用 [/Zi](z7-zi-zi-debug-information-format.md) 。|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|在建立偵錯程式庫時插入一個 PCH 參考。|
|[/Yu](yu-use-precompiled-header-file.md)|在建置時使用先行編譯標頭檔。|
|[/Z7](z7-zi-zi-debug-information-format.md)|產生 C 7.0 相容的偵錯資訊。|
|[/Za](za-ze-disable-language-extensions.md)|停用語言擴充功能。|
|[/Zc](zc-conformance.md)|指定下的標準行為[/Ze](za-ze-disable-language-extensions.md)。[/Za、 /Ze （停用語言擴充功能）](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|已取代。 啟用語言擴充功能。|
|[/Zf](zf.md)|在平行建置中產生時間改善 PDB。|
|[/Zg](zg-generate-function-prototypes.md)|已從 Visual C++ 2015 移除。 產生函式原型。|
|[/ZI](z7-zi-zi-debug-information-format.md)|將偵錯資訊包括在與「編輯後繼續」相容的程式資料庫中。|
|[/Zi](z7-zi-zi-debug-information-format.md)|產生完整偵錯資訊。|
|[/Zl](zl-omit-default-library-name.md)|從 .obj 檔案移除預設程式庫名稱 (僅適用於 x86)。|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|指定先行編譯標頭的記憶體配置上限。|
|[/Zp](zp-struct-member-alignment.md)|封裝結構成員。|
|[/Zs](zs-syntax-check-only.md)|僅檢查語法。|
|[/ZW](zw-windows-runtime-compilation.md)|產生輸出檔案，在 Windows 執行階段上執行。|

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)<br/>
[編譯器選項](compiler-options.md)<br/>
[設定編譯器選項](setting-compiler-options.md)