---
title: 特性指引最佳化
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341144"
---
# <a name="profile-guided-optimizations"></a>特性指引最佳化

特性指引最佳化 (PGO) 可讓您最佳化整個可執行檔的檔案，其中最佳化程式使用的.exe 或.dll 檔案的測試回合的資料。 將資料表示在實際執行環境中的程式可能的效能。

特性指引最佳化只適用於 x86 或 x64 原生的目標。 特性指引最佳化不適用於在通用語言執行平台執行的可執行檔。 即使您產生具有混合的原生和 managed 程式碼的組件 (使用 **/clr**編譯器選項)，您不能只是原生程式碼使用特性指引最佳化。 如果您嘗試使用這些選項設定在 IDE 中建置專案時，便會產生建置錯誤。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫才會作用中您指定的最佳化 **/Ob**， **/Os**，或 **/Ot**。 如需詳細資訊，請參閱 < [/Ob （內嵌函式展開）](reference/ob-inline-function-expansion.md)並[/Os、 /Ot （偏好小的程式碼、 偏好快的程式碼）](reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>若要最佳化您的應用程式的步驟

若要使用特性指引最佳化，請遵循以下步驟來最佳化您的應用程式：

- 編譯一或多個原始程式碼檔使用[/GL](reference/gl-whole-program-optimization.md)。

   每個模組，以建置 **/GL**來擷取執行階段行為的設定檔指引最佳化測試回合期間進行檢查。 特性指引最佳化組建中的每個模組不需要進行編譯 **/GL**。 不過，只有這些模組編譯 **/GL**進行檢測，稍後可供特性指引最佳化。

- 使用連結[/LTCG](reference/ltcg-link-time-code-generation.md)並[/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。

   使用這兩個 **/LTCG**並 **/GENPROFILE**或 **/FASTGENPROFILE**建立`.pgd`檔案時執行已檢測的應用程式。 測試回合資料加入至之後`.pgd`檔案，它可用來當做輸入下, 一個連結步驟 （建立最佳化映像）。 指定時 **/GENPROFILE**，您可以選擇性地加入**PGD =**_檔名_引數來指定非預設名稱或位置`.pgd`檔案。 組合 **/LTCG**並 **/GENPROFILE**或是 **/FASTGENPROFILE**連結器選項會取代已被取代 **/ltcg: pginstrument**連結器選項。

- 分析應用程式。

   每次分析的 EXE 工作階段結束，或分析的 DLL 卸載，`appname!N.pgc`建立檔案。 A`.pgc`檔案包含執行特定應用程式測試的相關資訊。 *appname*是您的應用程式的名稱和*N*號碼從 1 開始遞增數為依據的其他`appname!N.pgc`目錄中的檔案。 您可以刪除`.pgc`檔案如果測試回合不代表您想要最佳化的案例。

   在執行測試，您可以強制關閉目前開啟`.pgc`檔案並建立新`.pgc`檔案並[pgosweep](pgosweep.md)公用程式 （例如，當測試案例的結尾不符合應用程式關機）。

   您的應用程式也可以直接叫用 PGO 函式[PgoAutoSweep](pgoautosweep.md)，以擷取分析資料，在做為呼叫`.pgc`檔案。 它可讓您擷取資料所涵蓋的程式碼的更細微地控制您`.pgc`檔案。 如需如何使用此函式的範例，請參閱 < [PgoAutoSweep](pgoautosweep.md)文件。

   當您可以建立您已檢測的組建，根據預設時，資料收集是在非執行緒安全模式中，會比較快，但可能會不精確。 使用**精確**引數 **/GENPROFILE**或是 **/FASTGENPROFILE**，您可以指定資料收集在安全執行緒模式中，也就是更精確，但速度較慢。 此選項也會提供，如果您設定已被取代[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)環境變數，或已被取代 **/POGOSAFEMODE**連結器選項，當您建立已檢測的組建。

- 使用連結 **/LTCG**並 **/USEPROFILE**。

   使用這兩個 **/LTCG**並[/USEPROFILE](reference/useprofile.md)連結器選項，以建立最佳化映像。 此步驟會採用做為輸入`.pgd`檔案。 當您指定 **/USEPROFILE**，您可以選擇性地加入**PGD =**_檔名_引數來指定非預設的名稱或位置`.pgd`檔案。 您也可以使用已被取代，指定這個名稱 **/PGD**連結器選項。 組合 **/LTCG**並 **/USEPROFILE**取代已被取代 **/ltcg: pgoptimize**並**除了**連結器選項。

就更能夠建立最佳化的可執行檔，並在稍後判斷其他分析可能有助於建立更完善的映像。 如果已檢測的映像並將其`.pgd`檔案可供使用，，您可以執行其他測試回合，並重建最佳化與較新的映像`.pgd`檔案中，使用相同的 **/LTCG**和 **/USEPROFILE**連結器選項。

## <a name="optimizations-performed-by-pgo"></a>執行 PGO 所最佳化

特性指引最佳化包括這些檢查和增強功能：

- **內嵌**-例如，如果函式 A 經常呼叫函式 B，而函式 B 相對較小，則特性指引最佳化內嵌函式 B 在函式 a。

- **虛擬呼叫推測**-如果虛擬呼叫或透過函式指標，其他呼叫經常以某個函式，特性指引最佳化可以插入經常目標函式中，有條件地執行直接呼叫，直接呼叫可以內嵌。

- **暫存器配置**-根據設定檔資料產生更好的最佳化的暫存器配置。

- **基本區塊最佳化**-基本區塊最佳化可以讓經常執行基本區塊放在相同的頁面 （位置） 集合的指定範圍內暫時執行的。 它降至最低的頁數，記憶體額外負荷降到最低。

- **大小/速度最佳化**-程式耗費最多執行時間的函式可以針對速度最佳化。

- **函式配置**-根據呼叫歷程圖，以及剖析呼叫端/被呼叫端的行為，通常是在相同的執行路徑的函式會放在相同的區段。

- **條件式分支最佳化**-以值探查，特性指引最佳化可以找到 switch 陳述式中指定的值使用的頻率遠高於其他值。  然後此值會撤出 switch 陳述式。  可以透過完成相同`if`...`else`指示最佳化工具可以訂購其中`if`...`else`所以，請`if`或`else`區塊放在前面，根據哪個區塊更經常是 true。

- **無作用程式碼分離**-分析期間未呼叫的程式碼會移至 附加至區段集合結尾的特殊區段。 它可以有效地將經常使用的頁面從這一節。

- **EH 程式碼分離**-因為 EH 程式碼只有特別執行，它經常會移至不同的區段。 特性指引最佳化可以判斷只在例外條件發生例外狀況時，便會移。

- **記憶體內建函式**-是否擴充內建的或不取決於是否它經常被呼叫。 內建也可以根據移動或複製的區塊大小進行最佳化。

## <a name="next-steps"></a>後續步驟

深入的了解這些環境變數、 函數和工具可用於特性指引最佳化：

[特性指引最佳化的環境變數](environment-variables-for-profile-guided-optimizations.md)<br/>
這些變數用來指定執行階段行為的測試案例。 它們現在是已被取代，並由新的連結器選項所取代。 這份文件會示範如何從環境變數移至連結器選項。

[PgoAutoSweep](pgoautosweep.md)<br/>
您可以新增到您的應用程式，以提供更細緻的函式`.pgc`檔案資料擷取控制項。

[pgosweep](pgosweep.md)<br/>
將所有設定檔資料寫入命令列公用程式`.pgc`檔案，關閉`.pgc`檔案，並開啟新`.pgc`檔案。

[pgomgr](pgomgr.md)<br/>
新增設定檔資料，從一或多個命令列公用程式`.pgc`檔案到`.pgd`檔案。

[如何：合併在單一設定檔中的多個 PGO 設定檔](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
範例**pgomgr**使用量。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](reference/c-cpp-build-tools.md)
