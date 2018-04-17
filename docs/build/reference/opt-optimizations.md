---
title: -OPT （最佳化） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 928968803dc008eb39b3d0c52152c1f3b631a852
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="opt-optimizations"></a>/OPT (最佳化)
控制 LINK 在組建期間執行的最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## <a name="arguments"></a>引數  
 **REF** &AMP;#124; **NOREF**  
 **/Opt: ref**消除函式和資料從未參考。**/Opt: noref 則**函式和永不參考的資料會保留。  
  
 啟用 /opt: ref 時，LINK 會移除未參考的包裝函式和資料。 物件包含的封裝函式和資料 (Comdat) 如果編譯使用[/Gy](../../build/reference/gy-enable-function-level-linking.md)選項。 這種最佳化稱為可轉移 COMDAT 刪除。 根據預設， **/opt: ref**非偵錯組建中已啟用。 若要覆寫此預設值，而未參考的 Comdat 保留在程式中，指定**/opt: noref 則**。 您可以使用[/包含](../../build/reference/include-force-symbol-references.md)選項來覆寫對特定符號的移除。  
  
 當**/opt: ref**明確或預設值，之有限形式的已啟用**/opt: icf**啟用只摺疊相同函式。 如果您想**/opt: ref**但不是**/opt: icf**，您必須指定**/opt: ref、 NOICF**或**/opt: noicf**。  
  
 如果[偵錯](../../build/reference/debug-generate-debug-info.md)指定的預設值為**/選擇**是**NOREF**，而且所有函式會保留在映像。 若要覆寫此預設值，並將偵錯組建最佳化，指定**/opt: ref**。 因為**/opt: ref**意味著**/opt: icf**，我們建議您也指定**/opt: noicf**保留偵錯組建中的相同函式。 這可讓您更容易讀取堆疊追蹤，並且在會摺疊在一起的函式中設定中斷點。 **/Opt: ref**選項會停用累加連結。  
  
 您必須明確地標記`const`為 COMDAT 資料; 請改用[__declspec （selectany)](../../cpp/selectany.md)。  
  
 指定**/opt: icf**不會啟用**/opt: ref**選項。  
  
 **ICF [=** `iterations` **] &AMP;#124; NOICF**   
 使用**/opt: icf [=**`iterations`**]**執行相同的 COMDAT 摺疊。 重複的 COMDAT 可以從連結器輸出中移除。 選擇性 `iterations` 參數會指定要周遊符號找出重複項目的次數。 預設反覆項目數為二。 其他反覆項目可能會找出更多經由先前反覆項目中摺疊所揭露的重複項目。  
  
 連結器的行為方式時**/opt: ref**指定 — 與**ICF**作用中的預設值是-會**/opt: ref、 ICF**明確指定。 形式的**ICF**所啟用的**/opt: ref**單獨不會摺疊唯讀資料，包括.rdata、.pdata 和.xdata。 因此，這會在產生 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 的映像時，造成較少的函式摺疊，因為這些模組中的函式會更加依賴唯讀資料 (例如 .pdata 和 .xdata)。 若要取得完整**ICF**摺疊行為，明確指定**/opt: icf**。  
  
 若要在 Comdat 中放置函式，您使用**/Gy**編譯器選項; 將`const`資料，您將它宣告`__declspec(selectany)`。 如需如何指定摺疊的資料，請參閱[selectany](../../cpp/selectany.md)。  
  
 根據預設， **ICF**則是**REF**上。 若要覆寫此預設值，如果**REF**已指定，使用**NOICF**。 當**/opt: ref**中未指定偵錯組建，您必須明確指定**/opt: icf**以啟用 COMDAT 摺疊。 不過，因為**/opt: icf**可以合併相同的資料或函式，所以可以變更出現在堆疊追蹤中的函式名稱。 同時，也會使特定函式中無法設定中斷點或在偵錯工具中檢查某些資料，並會在您逐步執行程式碼時將您帶到未預期的函式。 因此，不建議您改用**/opt: icf**在偵錯組建除非較小的程式碼的優點大過這些缺點。  
  
> [!NOTE]
>  因為**/opt: icf**可能會導致相同的位址指派給不同的函式或唯讀資料成員 (`const`變數使用編譯的**/Gy**)，可能會中斷的程式而定函式或唯讀資料成員的唯一位址。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](../../build/reference/gy-enable-function-level-linking.md)。  
  
 **LBR** &AMP;#124; **NOLBR**  
 **/OPT:LBR**和**/OPT:NOLBR**選項只適用於 ARM 二進位檔。 由於某些 ARM 處理器分支指示的範圍有限，如果連結器偵測到跳至超出範圍的位址時，會以包含以實際目的地為目標的分支指令程式碼 "island" 位址取代分支指令的目的位址。 您可以使用**/OPT:LBR**最佳化長分支指令的偵測和整體程式碼大小降到最低的中繼程式碼島的放置。 **/OPT:NOLBR** ，指示連結器產生遇到，不需要最佳化長分支指令的程式碼島。  
  
 根據預設， **/OPT:LBR**未啟用累加連結時會設定選項。 如果您想要非累加連結，而不是長分支最佳化，指定**/OPT:NOLBR**。 **/OPT:LBR**選項會停用累加連結。  
  
## <a name="remarks"></a>備註  
 最佳化通常會減小映像的大小並且增加程式的速度，不過也會增加連結的時間。  
  
 您可以使用[/verbose](../../build/reference/verbose-print-progress-messages.md)選項可查看會被移除的函式**/opt: ref**和摺疊的函式**/opt: icf**。  
  
### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:ICF 或 OPT:REF 連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，依序展開**組態屬性**，**連結器**，**最佳化**。  
  
3.  修改其中一個屬性：  
  
    -   **啟用 COMDAT 摺疊**  
  
    -   **參考**  
  
### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:LBR 連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  輸入中的選項**其他選項**:  
  
     `/opt:lbr`  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 屬性。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
