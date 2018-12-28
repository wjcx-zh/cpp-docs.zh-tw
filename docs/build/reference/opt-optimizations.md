---
title: /OPT (最佳化)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: 1a6fa8b9c923ff697831c29b8004ce360baf7d77
ms.sourcegitcommit: ae2f71fe0d64f1a90ef722759fe93c82abc064ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53587885"
---
# <a name="opt-optimizations"></a>/OPT (最佳化)

控制 LINK 在組建期間執行的最佳化。

## <a name="syntax"></a>語法

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_反覆項目_] |**NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>引數

**REF** &AMP;#124; **NOREF**

**/Opt: ref**消除函式和永遠不會參考; 的資料 **/Opt: noref 則**函式和永不參考的資料會保留。

啟用 /opt: ref 時，LINK 會移除未參考的封裝函式和資料，又稱為*Comdat*。 這種最佳化稱為可轉移 COMDAT 刪除。 **/Opt: ref**選項也會停用累加連結。

內嵌函式和類別宣告內定義的成員函式都 Comdat。 所有目的檔中的函式會結合成為 Comdat 如果來編譯[/Gy](../../build/reference/gy-enable-function-level-linking.md)選項。 要放置**const** Comdat 中的資料，您必須將它宣告使用`__declspec(selectany)`。 如需如何指定要移除或摺疊的資料，請參閱[selectany](../../cpp/selectany.md)。

根據預設， **/opt: ref**除非已啟用連結器 **/opt: noref**或是[/偵錯](../../build/reference/debug-generate-debug-info.md)指定。 若要覆寫此預設值，並保留未參考的 Comdat 程式中，指定 **/opt: noref 則**。 您可以使用[/include](../../build/reference/include-force-symbol-references.md)選項來覆寫特定符號的移除。

如果[/偵錯](../../build/reference/debug-generate-debug-info.md)指定的預設值為 **/opt**是**NOREF**，而且所有函式都會保留在映像。 若要覆寫此預設值，並最佳化偵錯組建中，指定 **/opt: ref**。 這可以減少您的可執行檔的大小，而且可以是有用的最佳化，甚至是在偵錯組建。 我們建議您也指定 **/opt: noicf**保留相同的函式在偵錯組建。 這可讓您更容易讀取堆疊追蹤，並且在會摺疊在一起的函式中設定中斷點。

**ICF**\[**=**_反覆項目_] &#124; **NOICF**

使用**ICF**\[**=**_反覆項目_] 來執行相同的 COMDAT 摺疊。 重複的 COMDAT 可以從連結器輸出中移除。 選擇性*反覆項目*參數會指定要周遊的重複項目符號的次數。 反覆項目中的預設數目是 1。 其他反覆項目可能會找出更多經由先前反覆項目中摺疊所揭露的重複項目。

根據預設， **/opt: icf**已啟用連結器中，除非 **/opt: noicf**或是[/偵錯](../../build/reference/debug-generate-debug-info.md)指定。 若要覆寫此預設值，並在程式中摺疊時，防止 Comdat，請指定 **/opt: noicf**。

在偵錯組建中，您必須明確指定 **/opt: icf**啟用 COMDAT 摺疊。 不過，因為 **/opt: icf**可以合併相同的資料或函式，所以可以變更會出現在堆疊追蹤的函式名稱。 它也可以設定成不可能在某些函式中設定中斷點，或檢查偵錯工具中的部分資料，並帶您進入未預期的函式時您逐步執行程式碼。 程式碼的行為相同，但偵錯工具簡報可以是很令人困惑。 因此，我們執行不建議您使用 **/opt: icf**在偵錯組建除非較小的程式碼的優點大過這些缺點。

> [!NOTE]
> 因為 **/opt: icf**可能會導致相同的位址指派給不同的函式或唯讀資料成員 (也就是**const**變數時使用編譯 **/Gy**)，它可以中斷的程式，取決於函式或唯讀資料成員的唯一位址。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](../../build/reference/gy-enable-function-level-linking.md)。

**LBR** &AMP;#124; **NOLBR**

**/OPT:LBR**並 **/OPT:NOLBR**選項只適用於 ARM 二進位檔。 由於某些 ARM 處理器分支指示的範圍有限，如果連結器偵測到跳至超出範圍的位址時，會以包含以實際目的地為目標的分支指令程式碼 "island" 位址取代分支指令的目的位址。 您可以使用 **/OPT:LBR**最佳化長分支指令的偵測和整體的程式碼大小降到最低的中繼程式碼島的放置。 **/OPT:NOLBR**會指示連結器產生長分支指令的程式碼島，他們發現，不需要最佳化。

根據預設， **/OPT:LBR**未啟用累加連結時，設定選項。 如果您想要非累加連結，而不是長分支最佳化，指定 **/OPT:NOLBR**。 **/OPT:LBR**選項會停用累加連結。

## <a name="remarks"></a>備註

在命令列使用時，連結器會預設為**ICF，/opt: ref，LBR**。 如果 **/debug**指定，預設值是 **/opt: noref NOICF，NOLBR**。

**/Opt**最佳化通常減少映像大小，以及增加程式的速度。 這些增強功能可能很長，在較大的程式中，這也是為什麼在零售組建的預設啟用。

連結器最佳化，採用額外的時間，但最佳化程式碼還能節省的時間，當連結器有較少的重新配置，若要修正，並建立較小的最終映像，並將儲存更多的時間有較少的偵錯資訊來處理和寫入 PDB。 啟用最佳化時，它可能會導致更快速的連結時間整體來說，因為在分析中的小型額外成本可能會超過所節省的連結器經過較小的二進位檔的時間位移。

**/Opt**指定引數會放在一起，並以逗號分隔。 比方說，而不是 **/opt: ref /opt: noicf**，您可以指定 **/opt: ref、 NOICF**。

您可以使用[/verbose](../../build/reference/verbose-print-progress-messages.md)連結器選項，以查看會移除的函式 **/opt: ref**和 摺疊的函式 **/opt: icf**。

**/Opt**引數通常已為使用建立的專案**新的專案**對話方塊在 Visual Studio IDE 中，而且通常有不同的值進行偵錯和發行組態。 如果未不設定任何值，這些連結器選項，在您的專案中，您可能會取得專案預設值，可能會不同於在命令列連結器所使用的預設值。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:ICF 或 OPT:REF 連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **最佳化**屬性頁。

1. 修改其中一個屬性：

   - **啟用 COMDAT 摺疊**

   - **參考**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:LBR 連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**:

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 屬性。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)
