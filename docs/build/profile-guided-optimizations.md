---
title: 特性指引最佳化
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: efa4c35810f6272b89ff11cd1c890a7f535cfc1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232725"
---
# <a name="profile-guided-optimizations"></a>特性指引最佳化

特性指引優化（PGO）可讓您將整個可執行檔優化，其中優化工具會從 .exe 或 .dll 檔案的測試回合使用資料。 資料代表生產環境中可能的程式效能。

特性指引優化僅適用于 x86 或 x64 原生目標。 特性指引優化不適用於在 common language runtime 上執行的可執行檔。 即使您產生具有混合原生和 managed 程式碼的元件（使用 **/clr**編譯器選項），您也無法只在機器碼上使用特性指引優化。 如果您嘗試使用在 IDE 中設定的這些選項來建立專案，則會產生組建錯誤。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫優化，如果您指定 **/Ob**、 **/os**或 **/ot**，則會生效。 如需詳細資訊，請參閱[/Ob （內嵌函式展開）](reference/ob-inline-function-expansion.md)和[/os、/Ot （偏好小型程式碼、偏好快速程式碼）](reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>優化應用程式的步驟

若要使用特性指引優化，請遵循下列步驟來優化您的應用程式：

- 使用[/gl](reference/gl-whole-program-optimization.md)編譯一或多個原始程式碼檔。

   以 **/gl**建立的每個模組都可以在特性指引優化測試回合期間進行檢查，以捕捉執行時間行為。 特性指引優化組建中的每個模組都不需要使用 **/gl**進行編譯。 不過，只有以 **/gl**編譯的模組，才會進行檢測，並在稍後提供特性指引優化。

- 使用[/ltcg](reference/ltcg-link-time-code-generation.md)和[/GENPROFILE 或/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)進行連結。

   **/GENPROFILE**當執行 **/LTCG** **/FASTGENPROFILE** `.pgd` 檢測的應用程式時，同時使用/ltcg 和/GENPROFILE 或/FASTGENPROFILE 建立檔案。 將測試回合資料新增至檔案之後 `.pgd` ，就可以使用它做為下一個連結步驟的輸入（建立優化的映射）。 指定 **/GENPROFILE**時，您可以選擇性地加入**PGD =**_filename_引數來指定檔案的非預設名稱或位置 `.pgd` 。 **/Ltcg**和 **/GENPROFILE**或 **/FASTGENPROFILE**連結器選項的組合會取代已被取代的 **/ltcg： PGINSTRUMENT**連結器選項。

- 分析應用程式。

   每次分析的 EXE 會話結束，或卸載已剖析的 DLL 時， `appname!N.pgc` 就會建立一個檔案。 檔案 `.pgc` 包含特定應用程式測試回合的相關資訊。 *appname*是您應用程式的名稱， *N*是從1開始的數位，根據目錄中的其他檔案數目遞增 `appname!N.pgc` 。 `.pgc`如果測試回合不代表您想要優化的案例，您可以刪除檔案。

   在測試回合期間，您可以強制關閉目前開啟的檔案 `.pgc` ，並 `.pgc` 使用[pgosweep](pgosweep.md)公用程式建立新檔案（例如，當測試案例結束與應用程式關閉不一致時）。

   您的應用程式也可以直接叫用 PGO 函式[PgoAutoSweep](pgoautosweep.md)，以在呼叫時將設定檔資料視為檔案來捕捉 `.pgc` 。 它可以讓您更精確地控制檔案中的已捕獲資料所涵蓋的程式碼 `.pgc` 。 如需如何使用此函式的範例，請參閱[PgoAutoSweep](pgoautosweep.md)檔。

   當您建立已檢測的組建時，根據預設，資料收集會以非執行緒安全模式完成，這會更快速，但可能不精確。 藉由使用 **/GENPROFILE**或 **/FASTGENPROFILE**的**確切**引數，您可以線上程安全模式中指定資料收集，這會更精確，但速度較慢。 如果您在建立已檢測的組建時，設定了已淘汰的[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)環境變數或已淘汰的 **/POGOSAFEMODE**連結器選項，也可以使用此選項。

- 使用 **/ltcg**和 **/USEPROFILE**連結。

   請同時使用 **/ltcg**和[/USEPROFILE](reference/useprofile.md)連結器選項來建立優化的映射。 此步驟會將檔案作為輸入 `.pgd` 。 當您指定 **/USEPROFILE**時，您可以選擇性地加入**PGD =**_filename_引數來指定檔案的非預設名稱或位置 `.pgd` 。 您也可以使用已被取代的 **/PGD**連結器選項來指定此名稱。 **/Ltcg**和 **/USEPROFILE**的組合會取代已被取代的 **/ltcg： PGOPTIMIZE**和 **/ltcg： PGUPDATE**連結器選項。

您甚至可以建立優化的可執行檔，並在稍後判斷額外的分析功能，以建立更優化的映射。 如果已檢測的映射及其檔案 `.pgd` 可供使用，您可以 `.pgd` 使用相同的 **/ltcg**和 **/USEPROFILE**連結器選項，執行其他測試回合，並使用較新的檔案重建優化的映射。

> [!NOTE]
> `.pgc`和檔案 `.pgd` 都是二進位檔案類型。 如果儲存在原始檔控制系統中，請避免任何可能對文字檔進行的自動轉換。

## <a name="optimizations-performed-by-pgo"></a>PGO 所執行的優化

特性指引優化包含這些檢查和改善：

- **內嵌**-例如，如果函式經常呼叫函式 b，而函式 b 相對較小，則函數 a 中的特性指引優化內嵌函數 b。

- **虛擬呼叫推理**-如果虛擬呼叫或透過函式指標的其他呼叫經常以某個函式為目標，特性指引優化可以將有條件的直接呼叫插入至經常目標的函式，而直接呼叫可以內嵌。

- **註冊**配置-根據分析資料的優化會產生更好的暫存器配置。

- **基本區塊**優化-基本區塊優化可讓暫時在指定框架內執行的常用基本區塊，放在相同的一組頁面（位置）中。 它可將使用的頁面數目降至最低，這可將記憶體額外負荷降到最低。

- **大小/速度優化**-程式花費最多執行時間的函式可以針對速度優化。

- **函數**配置-根據呼叫圖形和分析的呼叫端/被呼叫端行為，通常會沿著相同執行路徑的函數會放在相同的區段中。

- **條件式分支優化**-使用值探查，特性指引優化可以找出 switch 語句中指定的值是否使用的頻率高於其他值。  然後此值會撤出 switch 陳述式。  也可以使用 **`if`** ... **`else`** 指示，讓優化工具可以排序 ...， **`if`** **`else`** 以便 **`if`** **`else`** 先放置或區塊，視哪一個區塊較常為 true 而定。

- 無作用程式**代碼分離**-分析期間未呼叫的程式碼會移到附加至區段集合結尾的特殊區段。 它會有效地將此區段保留在經常使用的頁面中。

- **Eh 程式碼分離**-因為 eh 程式碼只會特別執行，所以通常會移至個別的區段。 當特性指引優化可以判斷例外狀況只會發生在例外狀況時，就會移動它。

- **記憶體內建函式**-擴充內建與否取決於是否經常呼叫它。 內建也可以根據移動或複製的區塊大小進行最佳化。

## <a name="next-steps"></a>後續步驟

深入瞭解您可以在特性指引優化中使用的環境變數、函式和工具：

[特性指引最佳化的環境變數](environment-variables-for-profile-guided-optimizations.md)<br/>
這些變數是用來指定測試案例的執行時間行為。 它們現在已被取代，並由新的連結器選項取代。 本檔說明如何從環境變數移至連結器選項。

[PgoAutoSweep](pgoautosweep.md)<br/>
您可以新增至應用程式的函式，以提供更細緻的檔案 `.pgc` 資料捕獲控制。

[pgosweep](pgosweep.md)<br/>
一種命令列公用程式，可將所有設定檔資料寫入檔案 `.pgc` 、關閉檔案 `.pgc` ，然後開啟新的檔案 `.pgc` 。

[pgomgr](pgomgr.md)<br/>
一種命令列公用程式，可將一或多個檔案中的設定檔資料新增 `.pgc` 至檔案 `.pgd` 。

[作法：將多個 PGO 設定檔合併至單一設定檔](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
**Pgomgr**使用方式的範例。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](reference/c-cpp-build-tools.md)
