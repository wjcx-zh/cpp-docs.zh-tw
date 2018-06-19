---
title: 特性指引最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d6de281097232b1b8abc10a103af9c186e3550
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379402"
---
# <a name="profile-guided-optimizations"></a>特性指引最佳化

特性指引最佳化可讓您最佳化輸出檔案，其中最佳化程式使用來自測試的資料以執行 .exe 或 .dll 檔。 資料表示程式如何在實際執行環境中執行。

特性指引最佳化只適用於 x86 或 x64 原生目標。 特性指引最佳化不適用於在通用語言執行平台執行的輸出檔。 即使您產生具有混合的原生和 managed 程式碼的組件 (使用 **/clr**編譯器選項)，您無法對單純原生程式碼使用特性指引最佳化。 如果您嘗試建置專案時使用這些選項在 IDE 中設定，則建置會產生錯誤。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫原本是實際上是如果您指定的最佳化**須遵循 /Ob**， **/Os**，或 **/Ot**。 如需詳細資訊，請參閱[須遵循 /Ob （內嵌函式展開）](../../build/reference/ob-inline-function-expansion.md)和[/Os、 /Ot （偏好小的程式碼、 偏好快的程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>若要最佳化您的應用程式的步驟

若要使用特性指引最佳化，請遵循以下步驟來最佳化您的應用程式：

- 編譯一個或多個原始程式碼檔使用[/GL](../../build/reference/gl-whole-program-optimization.md)。

   由建置的每個模組 **/GL**擷取執行階段行為的特性指引最佳化測試回合期間進行檢查。 特性指引最佳化組建中的每個模組就不需要進行編譯 **/GL**。 不過，只有那些模組編譯 **/GL**會檢測，稍後可供特性指引最佳化。

- 連結使用[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)和[/GENPROFILE 或 /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。

   使用這兩個 **/LTCG**和 **/GENPROFILE**或 **/FASTGENPROFILE**已檢測的應用程式執行時建立的.pgd 檔。 測試回合資料加入至 .pgd 檔之後，它可以做為下一個連結步驟的輸入 (建立最佳化映像)。 當指定 **/GENPROFILE**，您可以選擇性地加入**PGD =**_filename_引數來指定非預設名稱或位置為.pgd 檔。 組合 **/LTCG**和 **/GENPROFILE**或 **/FASTGENPROFILE**連結器選項會取代已被取代 **/ltcg: pginstrument**連結器選項。

- 分析應用程式。

   每次分析的 EXE 工作階段結束或分析的 DLL 已卸載*appname*！ #.pgc 檔案建立。 .pgc 檔包含特定應用程式測試回合的相關資訊。 # 是從 1 開始遞增的其他數目為基礎的數字*appname*！ #.pgc 檔案的目錄中。 如果測試回合不代表您想要最佳化的案例，您可以刪除 .pgc 檔案。

   在測試回合中，您可以強制關閉目前開啟的.pgc 檔案的和新的.pgc 檔案，以建立[pgosweep](../../build/reference/pgosweep.md)公用程式 （例如，當與應用程式關閉不一致的測試案例結束）。

   您的應用程式也會直接叫用的 PGO 函式， [PgoAutoSweep](pgoautosweep.md)，以擷取分析資料，於呼叫的.pgc 檔案。 這麼做可以讓您更細微地控制.pgc 檔案中擷取的資料所涵蓋的程式碼。 如需如何使用這個函式的範例，請參閱[PgoAutoSweep](pgoautosweep.md)文件。

   當您建立您檢測的建置中，依預設時，資料收集會進行非執行緒安全模式，會較快，但可能不完全正確。 使用**精確**引數 **/GENPROFILE**或 **/FASTGENPROFILE**，您可以指定資料收集在具備執行緒安全模式中，也就是更精確，但速度較慢。 這個選項也是當您設定已被取代[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)環境變數，或已被取代 **/POGOSAFEMODE**連結器選項，當您建立您的檢測的建置。

- 連結使用 **/LTCG**和 **/USEPROFILE**。

   同時使用 **/LTCG**和[/USEPROFILE](useprofile.md)連結器選項，以建立最佳化映像。 這個步驟會採用做為輸入 .pgd 檔案。 當您指定 **/USEPROFILE**，您可以選擇性地加入**PGD =**_filename_引數來指定非預設的名稱或位置為.pgd 檔。 您也可以使用已被取代，指定這個名稱 **/PGD**連結器選項。 組合 **/LTCG**和 **/USEPROFILE**取代已被取代 **/ltcg: pgoptimize**和**除了**連結器選項。

甚至可以建立最佳化的輸出檔，並在稍後判斷其他分析可能有助於建立更完善的映像。 如果已檢測的映像和及其.pgd 檔案可用，您可以執行其他測試回合，並重建較新的.pgd 檔中，使用相同的最佳化的映像 **/LTCG**和 **/USEPROFILE**連結器選項.

## <a name="optimizations-performed-by-pgo"></a>執行的 PGO 最佳化

以下是特性指引最佳化的清單：

- **內嵌**-例如，如果有函式 A 經常呼叫函式 B，以及函式 B 是相當小，則特性指引最佳化會將函式 a 中的內嵌函式 B

- **虛擬呼叫推測**-如果虛擬呼叫或透過函式指標，其他呼叫經常以某個函式，特性指引最佳化可以插入有條件地執行的直接呼叫經常目標函式而且，可以內嵌直接呼叫。

- **暫存器配置**-使用設定檔資料會導致更好的暫存器配置最佳化。

- **基本區塊最佳化**-基本區塊最佳化可以讓經常執行基本區塊放在相同的頁面 （位置） 集合的指定範圍內暫時執行的。 這會儘可能減少所用的頁面，因此將記憶體額外負荷降至最低。

- **大小/速度最佳化**-程式耗費大量時間的函式可以針對速度最佳化。

- **函式配置**-根據呼叫歷程圖和分析的呼叫端/被呼叫端行為，通常是在相同執行路徑的函式會放在相同的區段。

- **條件式分支最佳化**-以值探查，特性指引最佳化可以找到 switch 陳述式中指定的值使用高於其他值的頻率。  然後此值會撤出 switch 陳述式。  可以對 if/else 指示進行相同作業，其中最佳化程式可以排序 if/else，根據哪個區塊更經常為 true，將 if 或 else 區塊放在前面。

- **無作用程式碼分離**-分析期間未呼叫的程式碼移到附加至區段集合結尾的特殊區段。 這可以有效地將此區段保持在經常使用的頁面之外。

- **EH 程式碼分離**-的 EH 程式碼，特別執行經常會移至不同的區段時特性指引最佳化可以判斷只在例外條件發生例外狀況。

- **記憶體內建函式**-擴充的內建函式可以更理想地決定如果可以判斷如果內建函式經常被呼叫。 內建也可以根據移動或複製的區塊大小進行最佳化。

如果您使用 Visual Studio 2013，您可以使用自動化[特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)以簡化和加速 Visual Studio 中的最佳化程序的效能和診斷中樞中的 Visual c + +。 此外掛程式不是在較新版本的 Visual Studio。

## <a name="next-steps"></a>後續步驟

深入了解這些環境變數、 函數和工具可用於特性指引最佳化：

[特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
這些變數可以用來指定測試案例的執行階段行為。 已被取代為新的連結器選項。讀取此選項可協助您從環境變數至連結器選項。

[PgoAutoSweep](pgoautosweep.md)<br/>
您可以將它加入至您的應用程式提供更細緻的.pgc 檔案資料擷取控制項函式。

[pgosweep](../../build/reference/pgosweep.md)<br/>
將所有設定檔資料寫入至.pgc 檔案，命令列公用程式會關閉.pgc 檔案，並開啟新的.pgc 檔案。

[pgomgr](../../build/reference/pgomgr.md)<br/>
將設定檔資料從一個或多個.pgc 檔案加入至.pgd 檔命令列公用程式。

[如何： 合併多個 PGO 設定檔至單一設定檔](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)的範例**pgomgr**使用量。

## <a name="see-also"></a>另請參閱

[C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)
