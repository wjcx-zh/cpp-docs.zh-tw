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
ms.openlocfilehash: 5c0ab3579fcb9633c435305a8b02b0c3f73d7a6f
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825700"
---
# <a name="opt-optimizations"></a>/OPT (最佳化)

控制 LINK 在組建期間執行的最佳化。

## <a name="syntax"></a>語法

> **/OPT：**{**REF** | **NOREF**} \
> **/Opt：**{**ICF**[**=**_反復_專案] |**NOICF**}\
> **/OPT：**{**LBR** | **NOLBR**}

## <a name="arguments"></a>引數

**REF** &#124; **NOREF**

**/Opt： REF**會排除從未參考的函式和資料;**/Opt： NOREF**會保留永遠不會參考的函式和資料。

當/OPT： REF 啟用時，LINK 會移除未參考的封裝函數和資料，稱為*comdat*。 這種最佳化稱為可轉移 COMDAT 刪除。 **/Opt： REF**選項也會停用增量連結。

在類別宣告內定義的內嵌函式和成員函式一律為 Comdat。 如果是使用[/gy](gy-enable-function-level-linking.md)選項編譯，則會將物件檔案中的所有函式都設為 comdat。 若要將**const**資料放在 comdat 中，您必須使用`__declspec(selectany)`來宣告它。 如需有關如何指定要移除或折迭之資料的詳細資訊，請參閱[selectany](../../cpp/selectany.md)。

根據預設，連結器會啟用 **/opt： REF** ，除非指定 **/opt： NOREF**或[/debug](debug-generate-debug-info.md) 。 若要覆寫此預設值，並在程式中保留未參考的 Comdat，請指定 **/opt： NOREF**。 您可以使用[/INCLUDE](include-force-symbol-references.md)選項來覆寫特定符號的移除。

如果指定[/debug](debug-generate-debug-info.md) ， **/opt**的預設值會是**NOREF**，而且所有函式都會保留在影像中。 若要覆寫這個預設值並優化 debug 組建，請指定 **/opt： REF**。 這可以減少可執行檔的大小，而且即使在 debug 組建中也是有用的優化。 我們建議您也指定 **/opt： NOICF** ，以在偵錯工具組建中保留相同的函式。 這可讓您更容易讀取堆疊追蹤，並且在會摺疊在一起的函式中設定中斷點。

**ICF** \[ICF**=** 反復_專案] &#124;_ **NOICF**

使用 [ **ICF**\[**=** 反復_專案] 來_執行相同的 COMDAT 折迭。 重複的 COMDAT 可以從連結器輸出中移除。 *選擇性的*反復專案參數會指定要跨越符號以進行重複的次數。 預設的反覆運算次數為1。 其他反覆項目可能會找出更多經由先前反覆項目中摺疊所揭露的重複項目。

根據預設，連結器會啟用 **/opt： ICF** ，除非指定 **/opt： NOICF**或[/debug](debug-generate-debug-info.md) 。 若要覆寫此預設值，並防止 Comdat 在程式中折迭，請指定 **/opt： NOICF**。

在 debug 組建中，您必須明確指定 **/opt： ICF** ，以啟用 COMDAT 折迭。 不過，因為 **/opt： ICF**可以合併相同的資料或函式，所以可以變更堆疊追蹤中出現的函式名稱。 它也可能會讓您無法在某些函式中設定中斷點，或在偵錯工具中檢查某些資料，而且當您逐步執行程式碼時，會將您帶到非預期的函數。 程式碼的行為完全相同，但偵錯工具的呈現可能非常令人困惑。 因此，我們不建議您在 debug 組建中使用 **/opt： ICF** ，除非較小的程式碼的優點超過這些缺點。

> [!NOTE]
> 由於 **/opt： ICF**可能會導致相同的位址指派給不同的函式或唯讀資料成員（也就是使用 **/gy**編譯時的**const**變數），因此可能會中斷相依于函數或唯讀資料成員之唯一位址的程式。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](gy-enable-function-level-linking.md)。

**LBR** &#124; **NOLBR**

**/Opt： LBR**和 **/opt： NOLBR**選項僅適用于 ARM 二進位檔。 由於特定 ARM 處理器分支指示的範圍有限，因此如果連結器偵測到跳到超出範圍的位址，它會將分支指令的目的地位址取代為代碼 "島" 的位址，其中包含以實際目的地為目標的分支指令。 您可以使用 **/opt： LBR**來優化長分支指令的偵測和中繼程式碼島的放置，將整體程式碼大小降到最低。 **/Opt： NOLBR**會指示連結器在遇到長分支指令時產生程式碼島，而不需要優化。

根據預設，當未啟用累加連結時，會設定 **/opt： LBR**選項。 如果您想要非累加連結，但不是長分支優化，請指定 **/opt： NOLBR**。 **/Opt： LBR**選項會停用增量連結。

## <a name="remarks"></a>備註

在命令列使用時，連結器預設為 **/opt： REF，ICF，LBR**。 如果指定 **/debug** ，預設值為 **/opt： NOREF、NOICF、NOLBR**。

**/Opt**優化通常會減少映射大小並增加程式速度。 這些改良功能在較大型的程式中可能很重要，這就是為什麼針對零售組建預設為啟用。

連結器優化會事先耗費額外的時間，但優化的程式碼也會節省連結器重設較少的時間以進行修正，並建立較小的最終影像，並節省更多時間來處理和寫入 PDB 的 debug 資訊較少。 啟用優化時，可能會導致連結時間變得更快，因為分析的小型額外成本可能會比在連結器傳遞較小的二進位檔中節省的時間還多。

**/Opt**引數可以指定在一起，並以逗號分隔。 例如，您可以指定 **/opt： ref、NOICF**，而不是 **/OPT： REF/opt： NOICF**。

您可以使用[/verbose](verbose-print-progress-messages.md)連結器選項來查看 **/opt： REF**所移除的函式，以及由 **/opt： ICF**所折迭的函數。

**/Opt**引數通常會針對使用 Visual Studio IDE 中 [**新增專案**] 對話方塊所建立的專案進行設定，而且在 debug 和發行設定中通常會有不同的值。 如果您專案中的這些連結器選項未設定任何值，則您可以取得專案預設值，這可能會與命令列上連結器所使用的預設值不同。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:ICF 或 OPT:REF 連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > **連結器** > **優化**] 屬性頁。

1. 修改其中一個屬性：

   - **啟用 COMDAT 摺疊**

   - **參考**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 OPT:LBR 連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [**連結器** > **命令列**] 屬性頁。

1. 在 [**其他選項**] 中輸入選項：

   `/opt:lbr` 或 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 屬性。

## <a name="see-also"></a>請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
