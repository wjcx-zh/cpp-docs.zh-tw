---
title: "特性指引最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2d72ddda460a88830f7f7692f4c9707fa3101a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimizations"></a>特性指引最佳化
特性指引最佳化可讓您最佳化輸出檔案，其中最佳化程式使用來自測試的資料以執行 .exe 或 .dll 檔。 資料表示程式如何在實際執行環境中執行。  
  
 特性指引最佳化只適用於 x86 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 原生目標。 特性指引最佳化不適用於在 Common Language Runtime 上執行的輸出檔案。 即使您產生具有混合的原生和 managed 程式碼的組件 (以編譯**/clr**)，您無法對單純原生程式碼使用特性指引最佳化。 如果您在 IDE 中嘗試使用這些選項設定來建置專案，會發生建置錯誤。  
  
> [!NOTE]
>  從分析測試回合所收集的資訊將會覆寫原本是實際上是如果您指定的最佳化**須遵循 /Ob**， **/Os**，或**/Ot**。 如需詳細資訊，請參閱[須遵循 /Ob （內嵌函式展開）](../../build/reference/ob-inline-function-expansion.md)和[/Os、 /Ot （偏好小的程式碼、 偏好快的程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  
  
 在效能及診斷中樞中使用適用於 Visual C++ 外掛程式的自動化特性指引最佳化，以簡化和加速 Visual Studio 內的最佳化程序，或者您可以在 Visual Studio 中或命令列上手動執行最佳化步驟。 我們建議使用外掛程式，因為比較容易使用。 如需如何取得外掛程式，並用來最佳化您的應用程式資訊，請參閱[特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
 特性指引最佳化外掛程式和手動特性指引最佳化兩者都遵循以下步驟來最佳化您的應用程式：  
  
-   編譯一個或多個原始程式碼檔使用[/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
     使用 /GL 建置的每個模組可以在特性指引最佳化測試回合期間進行檢查，以擷取執行階段行為。 特性指引最佳化組建中的每個模組不需要以 /GL 編譯。 不過，只會檢測以 /GL 編譯的模組，稍後可供特性指引最佳化使用。  
  
-   連結使用[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)和[/GENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。  
  
     使用 /LTCG 和 /genprofile 時，會建立空白的.pgd 檔。 測試回合資料加入至 .pgd 檔之後，它可以做為下一個連結步驟的輸入 (建立最佳化映像)。 當您指定 /genprofile 時，您可以選擇性地加入： PGD =`filename`指定非預設名稱或為.pgd 檔的位置。  
  
-   分析應用程式。  
  
     每次分析的 EXE 工作階段結束或分析的 DLL 已卸載*appname*！ #.pgc 檔案建立。 .pgc 檔包含特定應用程式測試回合的相關資訊。 # 是從 1 開始遞增的其他數目為基礎的數字*appname*！ #.pgc 檔案的目錄中。 如果測試回合不代表您想要最佳化的案例，您可以刪除 .pgc 檔案。  
  
     在測試回合中，您可以強制關閉目前開啟的.pgc 檔案的和新的.pgc 檔案，以建立[pgosweep](../../build/reference/pgosweep.md)公用程式 （例如，當與應用程式關閉不一致的測試案例結束）。  
  
     當您分析應用程式時，可以使用 `PogoSafeMode` 選項。 此選項可讓您指定以安全模式或快速模式分析應用程式。 如需有關這些模式的詳細資訊，請參閱[PogoSafeMode](../../build/reference/pogosafemode.md)。  
  
-   使用 /LTCG 和 /USEPROFILE 的連結。  
  
     使用 /LTCG 和 /USEPROFILE 建立最佳化映像。 這個步驟會採用做為輸入 .pgd 檔案。 當指定 /USEPROFILE，您可以選擇性地加入： PGD =`filename`指定非預設名稱或為.pgd 檔的位置。 如需詳細資訊，請參閱[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 甚至可以建立最佳化的輸出檔，並在稍後判斷其他分析可能有助於建立更完善的映像。 如果已檢測的映像及其 .pgd 檔案可供使用，您可以執行其他測試回合，並使用較新的 .pgd 檔案重新建置最佳化映像。  
  
 以下是特性指引最佳化的清單：  
  
-   **內嵌**-例如，如果有函式 A 經常呼叫函式 B，以及函式 B 是相當小，則特性指引最佳化會將函式 a 中的內嵌函式 B  
  
-   **虛擬呼叫推測**-如果虛擬呼叫或透過函式指標，其他呼叫經常以某個函式，特性指引最佳化可以插入有條件地執行的直接呼叫經常目標函式而且，可以內嵌直接呼叫。  
  
-   **暫存器配置**-使用設定檔資料會導致更好的暫存器配置最佳化。  
  
-   **基本區塊最佳化**-基本區塊最佳化可以讓經常執行基本區塊放在相同的頁面 （位置） 集合的指定範圍內暫時執行的。 這會儘可能減少所用的頁面，因此將記憶體額外負荷降至最低。  
  
-   **大小/速度最佳化**-程式耗費大量時間的函式可以針對速度最佳化。  
  
-   **函式配置**-根據呼叫歷程圖和分析的呼叫端/被呼叫端行為，通常是在相同執行路徑的函式會放在相同的區段。  
  
-   **條件式分支最佳化**-以值探查，特性指引最佳化可以找到 switch 陳述式中指定的值使用高於其他值的頻率。  然後此值會撤出 switch 陳述式。  可以對 if/else 指示進行相同作業，其中最佳化程式可以排序 if/else，根據哪個區塊更經常為 true，將 if 或 else 區塊放在前面。  
  
-   **無作用程式碼分離**-分析期間未呼叫的程式碼移到附加至區段集合結尾的特殊區段。 這可以有效地將此區段保持在經常使用的頁面之外。  
  
-   **EH 程式碼分離**-的 EH 程式碼，特別執行經常會移至不同的區段時特性指引最佳化可以判斷只在例外條件發生例外狀況。  
  
-   **記憶體內建函式**-擴充的內建函式可以更理想地決定如果可以判斷如果內建函式經常被呼叫。 內建也可以根據移動或複製的區塊大小進行最佳化。  
  
 在 IDE 中執行手動最佳化或命令列上的詳細資訊，請參閱[特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [手動特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [如何：將多個 PGO 設定檔合併至單一設定檔](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## <a name="see-also"></a>請參閱  
 [C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)