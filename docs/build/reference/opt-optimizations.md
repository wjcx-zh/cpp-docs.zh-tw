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
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336228"
---
# <a name="opt-optimizations"></a>/OPT (最佳化)

控制 LINK 在組建期間執行的最佳化。

## <a name="syntax"></a>語法

> **/選擇:**【**參考** | **NOREF**]<br/>
> **/OPT:**[**ICF**]**=**_反覆運算_|**NOICF**|<br/>
> **/OPT:**[**LBR** | **NOLBR**]

## <a name="arguments"></a>引數

**參考&#124;****諾夫雷**

**/OPT:REF**消除了從未引用的函數和數據;**/OPT:NOREF**保留從未引用的函數和數據。

啟用 /OPT:REF 後,LINK 將刪除未引用的打包函數和數據,稱為*COMDAT。* 這種最佳化稱為可轉移 COMDAT 刪除。 **/OPT:REF**選項還禁用增量連結。

在類聲明中定義的內聯函數和成員函數始終是 COMDAT。 如果使用[/Gy](gy-enable-function-level-linking.md)選項編譯物件檔中的所有函數,則將其製作為 COMDAT。 要將**const**資料放在 COMDAT`__declspec(selectany)`中,必須使用聲明數據。 有關如何指定資料進行刪除或折疊的資訊,請參閱[selectany](../../cpp/selectany.md)。

預設情況下 **,/OPT:REF**由連結器啟用,除非指定 **/OPT:NOREF**或[/DEBUG。](debug-generate-debug-info.md) 要覆寫此預設值並在程式中保留未參考的 COMDAT,請指定 **/OPT:NOREF**。 您可以使用[/INCLUDE](include-force-symbol-references.md)選項來覆蓋特定符號的刪除。

如果指定[/DEBUG,](debug-generate-debug-info.md)**則 /OPT**的預設值為**NOREF**,並且所有函數都保留在映射中。 要覆寫此預設值並優化除錯產生,請指定 **/OPT:REF**。 這可以減小可執行檔的大小,即使在調試生成中也可以進行有用的優化。 我們建議您也指定 **/OPT:NOICF**以在除錯生成中保留相同的函數。 這可讓您更容易讀取堆疊追蹤，並且在會摺疊在一起的函式中設定中斷點。

**ICF**\[**=**_發疊代_= &#124; **NOICF**

使用**ICF**\[**=**_的發運算_= 執行相同的 COMDAT 折疊。 重複的 COMDAT 可以從連結器輸出中移除。 可選*反覆運算*參數指定遍歷重複符號的次數。 默認反覆運算次數為 1。 其他反覆項目可能會找出更多經由先前反覆項目中摺疊所揭露的重複項目。

預設情況下 **,/OPT:ICF**由連結器啟用,除非指定 **/OPT:NOICF**或[/DEBUG。](debug-generate-debug-info.md) 要覆寫此預設值並防止在應用程式中折疊 COMDAT,請指定 **/OPT:NOICF**。

在除錯產生中,必須顯式指定 **/OPT:ICF**才能啟用 COMDAT 折疊。 但是,由於 **/OPT:ICF**可以合併相同的數據或函數,因此它可以更改堆疊跟蹤中顯示的函數名稱。 它還會使無法在某些函數中設置斷點或檢查調試器中的某些數據,並且在單步執行代碼時,可能會將您帶入意外的函數。 代碼的行為是相同的,但調試器表示可能非常混亂。 因此,我們不建議在調試生成中使用 **/OPT:ICF,** 除非較小的代碼的優點大於這些缺點。

> [!NOTE]
> 因為 **/OPT:ICF**會導致將同一位址分配給不同的函數或唯讀資料成員(即,使用 **/Gy**編譯時**的 const**變數),因此它可以破壞依賴於函數的唯一位址或唯讀資料成員的程式。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](gy-enable-function-level-linking.md)。

**LBR** &#124; **NOLBR**

**/OPT:LBR**和 **/OPT:NOLBR**選項僅適用於 ARM 二進位檔案。 由於某些 ARM 處理器分支指令的範圍有限,因此如果連結器檢測到跳轉到範圍外的位址,它將分支指令的目標位址替換為包含指向實際目標的分支指令的代碼"island"的位址。 您可以使用 **/OPT:LBR**優化長分支指令的檢測和中間代碼孤島的位置,以最小化總體代碼大小。 **/OPT:NOLBR**指示連結器在遇到長分支指令時生成代碼孤島,而不進行優化。

預設情況下,如果未啟用增量連結,則設置 **/OPT:LBR**選項。 如果需要非增量連結,但分支優化時間不長,請指定 **/OPT:NOLBR**。 **/OPT:LBR**選項禁用增量連結。

## <a name="remarks"></a>備註

在命令列使用時,連結器預設為 **/OPT:REF、ICF、LBR**。 若指定 **/DEBUG,** 則預設值為 **/OPT:NOREF、NOICF、NOLBR**。

**/OPT**優化通常會減小圖像大小並提高程式速度。 這些改進在較大的程式中可能很大,這就是為什麼默認情況下為零售生成啟用這些改進的原因。

Linker 優化確實需要額外的時間,但優化的代碼也會節省時間,當連結器的重新定位較少以進行修復並創建較小的最終映射時,當它具有較少的調試資訊來處理並寫入 PDB 時,它可以節省更多的時間。 啟用優化后,它可能會導致整體連結時間更快,因為分析中的少量額外成本可能會因連結器通過較小的二進位檔所節省的時間而抵消。

**/OPT**參數可以一起指定,用逗號分隔。 例如,您可以指定 **/OPT:REF,而不是** **:REF /OPT:NOICF。**

您可以使用[/VERBOSE](verbose-print-progress-messages.md)連結器選項查看 **/OPT:REF**刪除的函數以及 **/OPT:ICF**折疊的函數。

**/OPT**參數通常設置為使用 Visual Studio IDE 中的 **"新項目**"對話框創建的項目,並且通常具有不同的調試和發佈配置值。 如果專案中未為這些連結器選項設置任何值,則您可能會獲取專案預設值,這可能與命令列連結器使用的預設值不同。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:ICF 或 OPT:REF 連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**配置屬性** > **連結器** > **優化**屬性頁面。

1. 修改其中一個屬性：

   - **啟用 COMDAT 摺疊**

   - **參考**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:LBR 連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**設定屬性** > **連結器** > **命令列**屬性頁。

1. 在 **'其他選項**' 中輸入選項 :

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 屬性。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
