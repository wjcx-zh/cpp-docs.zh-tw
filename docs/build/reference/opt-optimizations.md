---
title: "/OPT (最佳化) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.OptimizeReferences"
  - "/opt"
  - "VC.Project.VCLinkerTool.OptimizeForWindows98"
  - "VC.Project.VCLinkerTool.EnableCOMDATFolding"
  - "VC.Project.VCLinkerTool.OptimizeFolding"
  - "VC.Project.VCLinkerTool.FoldingIterations"
  - "VC.Project.VCLinkerTool.OptimizeFoldingIterations"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OPT 連結器選項"
  - "LINK 工具 [C++], 控制最佳化"
  - "連結器 [C++], 最佳化"
  - "OPT 連結器選項"
  - "-OPT 連結器選項"
  - "最佳化, 連結器"
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /OPT (最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制 LINK 在組建期間執行的最佳化。  
  
## 語法  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## 引數  
 **REF** &#124; **NOREF**  
 **\/OPT:REF** 會排除永不參考的函式和 \(或\) 資料，而 **\/OPT:NOREF** 則會保留永不參考的函式和 \(或\) 資料。  
  
 啟用 \/OFT:REF 時，LINK 會移除未參考的封裝函式和資料。  如果物件是用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 選項編譯，就會含有封裝函式 \(COMDAT\) 與資料。  這種最佳化稱為可轉移 COMDAT 刪除。  依預設，**\/OPT:REF** 在非偵錯組建是啟用的。  若要覆寫這項預設，並且將未參考的 COMDAT 保留在程式中，請指定 **\/OPT:NOREF**。  您可以使用 [\/INCLUDE](../../build/reference/include-force-symbol-references.md) 選項，覆寫對特定符號的移除。  
  
 明確啟用或依預設啟用 **\/OPT:REF** 時，會啟用只摺疊相同函式之有限形式的 **\/OPT:ICF**。  如果您要的是 **\/OPT:REF** 而不是 **\/OPT:ICF** 時，則必須指定 **\/OPT:REF,NOICF** 或 **\/OPT:NOICF**。  
  
 如果指定 [\/DEBUG](../../build/reference/debug-generate-debug-info.md)，則 **\/OPT** 的預設值為 **NOREF**，而且所有函式都會保留在映像中。  若要覆寫此預設值，並將偵錯組建最佳化，請指定 **\/OPT:REF**。  由於 **\/OPT:REF** 中隱含 **\/OPT:ICF**，建議您同時指定 **\/OPT:NOICF** 以保留偵錯組建中相同的函式。  這可讓您更容易讀取堆疊追蹤，並且在會摺疊在一起的函式中設定中斷點。  **\/OPT:REF** 選項會停用累加連結。  
  
 您必須將 `const` 資料明確標記為 COMDAT，因此，請使用 [\_\_declspec\(selectany\)](../../cpp/selectany.md)。  
  
 指定 **\/OPT:ICF** 時不會啟用 **\/OPT:REF** 選項。  
  
 **ICF\[\=**  `iterations` **\] &#124; NOICF**  
 使用 **\/OPT:ICF\[\=**`iterations`**\]**，以執行相同的 COMDAT 摺疊。  重複的 COMDAT 可以從連結器輸出中移除。  選擇性 `iterations` 參數會指定要周遊符號找出重複項目的次數。  預設反覆項目數為二。  其他反覆項目可能會找出更多經由先前反覆項目中摺疊所揭露的重複項目。  
  
 當指定 **\/OPT:REF** 並且預設為 **ICF** 有效時，連結器的行為會與明確指定 **\/OPT:REF,ICF** 時有所不同。  只用 **\/OPT:REF** 所啟用的 **ICF** 形式不會摺疊唯讀資料，包括 .rdata、.pdata 和 .xdata。  因此，這會在產生 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 的映像時，造成較少的函式摺疊，因為這些模組中的函式會更加依賴唯讀資料 \(例如 .pdata 和 .xdata\)。  若要取得完整的 **ICF** 摺疊行為，請明確指定 **\/OPT:ICF**。  
  
 若要在 COMDAT 中放置函式，請使用 **\/Gy** 編譯器選項。若要放置 `const` 資料，則將其宣告為 `__declspec(selectany)`。  如需如何指定摺疊所用資料的詳細資訊，請參閱 [selectany](../../cpp/selectany.md)。  
  
 如果 **REF** 為開啟狀態，則 **ICF** 預設為開啟。  若要在指定 **REF** 時覆寫這項預設值，請使用 **NOICF**。  當偵錯組建中沒有指定 **\/OPT:REF** 時，您必須明確指定 **\/OPT:ICF** 以啟用 COMDAT 摺疊。  不過，因為 **\/OPT:ICF** 可以結合相同資料或函式，所以可以變更出現在堆疊追蹤中的函式名稱。  同時，也會使特定函式中無法設定中斷點或在偵錯工具中檢查某些資料，並會在您逐步執行程式碼時將您帶到未預期的函式。  因此，我們不建議您在偵測組建中使用 **\/OPT:ICF**，除非較小的程式碼的優點大過這些缺點。  
  
> [!NOTE]
>  由於 **\/OPT:ICF** 可能造成相同的位址被指派給不同的函式或唯讀資料成員 \(以 **\/Gy** 編譯的 `const` 變數\)，所以可能會使依賴獨特函式位址或唯讀資料成員的程式中斷。  如需詳細資訊，請參閱[\/Gy \(啟用函式階層連結\)](../../build/reference/gy-enable-function-level-linking.md)。  
  
 **LBR** &#124; **NOLBR**  
 **\/OPT:LBR** 和 **\/OPT:NOLBR** 選項只適用於 ARM 二進位檔。  由於某些 ARM 處理器分支指示的範圍有限，如果連結器偵測到跳至超出範圍的位址時，會以包含以實際目的地為目標的分支指令程式碼 "island" 位址取代分支指令的目的位址。  您可以使用 **\/OPT:LBR** 最佳化長分支指令的偵測和中繼程式碼島的放置，將整體程式碼大小降到最低。  **\/OPT:NOLBR** 會指示連結器在遇到長分支指令時產生程式碼島，不需要最佳化。  
  
 根據預設，未啟用累加連結時會設定 **\/OPT:LBR** 選項。  如果您想要非累加連結，而不是長分支最佳化，請指定 **\/OPT:NOLBR**。  **\/OPT:LBR** 選項會停用累加連結。  
  
## 備註  
 最佳化通常會減小映像的大小並且增加程式的速度，不過也會增加連結的時間。  
  
 您可以使用 [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 選項，查看由 **\/OPT:REF** 移除的函式，以及由 **\/OPT:ICF** 摺疊的函式。  
  
### 在 Visual Studio 開發環境中設定 OPT:ICF 或 OPT:REF 連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左方窗格中展開 \[**組態屬性**\]、\[**連結器**\]、\[**最佳化**\]。  
  
3.  修改其中一個屬性：  
  
    -   **啟用 COMDAT 摺疊**  
  
    -   **參考**  
  
### 在 Visual Studio 開發環境中設定 OPT:LBR 連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項：  
  
     `/opt:lbr`  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 屬性。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)