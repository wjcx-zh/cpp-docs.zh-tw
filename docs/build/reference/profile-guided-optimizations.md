---
title: "特性指引最佳化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "最佳化, 特性指引 [C++]"
  - "特性指引最佳化"
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 特性指引最佳化
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

特性指引最佳化可讓您最佳化輸出檔案，其中最佳化程式使用來自測試的資料以執行 .exe 或 .dll 檔。  資料表示程式如何在實際執行環境中執行。  
  
 特性指引最佳化只適用於 x86 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 原生目標。  特性指引最佳化不適用於在 Common Language Runtime 上執行的輸出檔案。  即使您產生具有混合的原生和 Managed 程式碼的組件 \(以 **\/clr** 編譯\)，您無法對單純的原生程式碼使用特性指引最佳化。  如果您在 IDE 中嘗試使用這些選項設定來建置專案，會發生建置錯誤。  
  
> [!NOTE]
>  從分析測試回合所收集的資訊會覆寫最佳化，這個最佳化在指定 **\/Ob**、**\/Os** 或 **\/Ot** 時才會生效。  如需詳細資訊，請參閱 [\/Ob \(內嵌函式展開\)](../../build/reference/ob-inline-function-expansion.md) 和 [\/Os、\/Ot \(偏好小的程式碼、偏好快的程式碼\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  
  
 在效能及診斷中樞中使用適用於 Visual C\+\+ 外掛程式的自動化特性指引最佳化，以簡化和加速 Visual Studio 內的最佳化程序，或者您可以在 Visual Studio 中或命令列上手動執行最佳化步驟。  我們建議使用外掛程式，因為比較容易使用。  如需如何取得外掛程式，並用來最佳化您的應用程式的詳細資訊，請參閱[特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
 特性指引最佳化外掛程式和手動特性指引最佳化兩者都遵循以下步驟來最佳化您的應用程式：  
  
-   使用 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯一或多個原始程式碼檔。  
  
     使用 \/GL 建置的每個模組可以在特性指引最佳化測試回合期間進行檢查，以擷取執行階段行為。  特性指引最佳化組建中的每個模組不需要以 \/GL 編譯。  不過，只會檢測以 \/GL 編譯的模組，稍後可供特性指引最佳化使用。  
  
-   以 [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) 連結。  
  
     \/LTCG:PGINSTRUMENT 會建立空白的.pgd 檔。  測試回合資料加入至 .pgd 檔之後，它可以做為下一個連結步驟的輸入 \(建立最佳化映像\)。  當指定 \/LTCG:PGINSTRUMENT 時，您可以選擇性地為 .pgd 檔指定具有非預設名稱或位置的 [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)。  
  
-   分析應用程式。  
  
     每次分析 EXE 工作階段結束時，或分析 DLL 卸載時，就會建立 *appname*\! \#.pgc 檔案。  .pgc 檔包含特定應用程式測試回合的相關資訊。  \# 是從 1 開始遞增的數字，根據目錄中其他 *appname*\! \#.pgc 檔案的數字。  如果測試回合不代表您想要最佳化的案例，您可以刪除 .pgc 檔案。  
  
     在測試回合中，您可以強制關閉目前開啟的 .pgc 檔案，然後使用 [pgosweep](../../build/reference/pgosweep.md) 公用程式建立新的 .pgc 檔案 \(例如，當測試案例結束與應用程式關閉不一致時\)。  
  
     當您分析應用程式時，可以使用 `PogoSafeMode` 選項。  此選項可讓您指定以安全模式或快速模式分析應用程式。  如需這些模式的詳細資訊，請參閱 [PogoSafeMode](../../build/reference/pogosafemode.md)。  
  
-   以 \/LTCG:PGOPTIMIZE 連結。  
  
     \/LTCG:PGOPTIMIZE 會建立最佳化映像。  這個步驟會採用做為輸入 .pgd 檔案。  如需詳細資訊，請參閱 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 甚至可以建立最佳化的輸出檔，並在稍後判斷其他分析可能有助於建立更完善的映像。  如果已檢測的映像及其 .pgd 檔案可供使用，您可以執行其他測試回合，並使用較新的 .pgd 檔案重新建置最佳化映像。  
  
 以下是特性指引最佳化的清單：  
  
-   **內嵌** \- 例如，如果有函式 A 經常呼叫函式 B，且函式 B 相對較小，則特性指引最佳化會在函式 A 中內嵌函式 B。  
  
-   **虛擬呼叫推測**  \- 如果虛擬呼叫或透過函式指標的其他呼叫經常以某個函式為目標，特性指引最佳化可以對經常目標函式插入有條件執行的直接呼叫，而且可以內嵌直接呼叫。  
  
-   **暫存器配置** \- 以分析資料最佳化來產生更理想的暫存器配置。  
  
-   **基本區塊最佳化** \- 基本區塊最佳化可以讓指定範圍內暫時執行的經常執行基本區塊放在一組相同的頁面 \(位置\)。  這會儘可能減少所用的頁面，因此將記憶體額外負荷降至最低。  
  
-   **大小\/速度最佳化**  \- 程式耗費大量時間的函式可以針對速度最佳化。  
  
-   **函式配置** – 根據呼叫圖形和分析的呼叫端\/被呼叫端行為，通常是在相同執行路徑的函式會放在相同的區段。  
  
-   **條件式分支最佳化** \- 以值探查，特性指引最佳化可以找到 switch 陳述式中指定的值的使用頻率是否遠高於其他值。  然後此值會撤出 switch 陳述式。  可以對 if\/else 指示進行相同作業，其中最佳化程式可以排序 if\/else，根據哪個區塊更經常為 true，將 if 或 else 區塊放在前面。  
  
-   **無作用程式碼分離**  \- 分析期間未呼叫的程式碼會移到附加至區段集合結尾的特殊區段。  這可以有效地將此區段保持在經常使用的頁面之外。  
  
-   **EH 程式碼分離** \- 當特性指引最佳化可以判斷只在例外條件之下發生例外狀況時，特別執行的 EH 程式碼經常會移至不同的區段。  
  
-   **記憶體內建** – 如果您可以判斷是否經常呼叫內建，則可以更理想地決定內建的擴充。  內建也可以根據移動或複製的區塊大小進行最佳化。  
  
 如需在 IDE 中或命令列上執行手動最佳化的詳細資訊，請參閱[逐步解說：使用特性指引最佳化](http://msdn.microsoft.com/zh-tw/6e36421b-ec8c-4626-9c29-fa5ffb6f27f8)。  
  
## 本章節內容  
 [特性指引最佳化外掛程式](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [如何：將多個 PGO 設定檔合併至單一設定檔](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)