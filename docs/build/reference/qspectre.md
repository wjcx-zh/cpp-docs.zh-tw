---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e8d03075a980a9b9c345ce351413e39a3c3444cb
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808824"
---
# <a name="qspectre"></a>/Qspectre

指定產生指示的編譯器，以減少特定 Spectre 變體 1 的安全性弱點。

## <a name="syntax"></a>語法

> **/Qspectre**

## <a name="remarks"></a>備註

**/Qspectre** 選項已在 Visual Studio 2017 15.5.5 版和更新版本中提供，也可透過 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre) 在 Visual Studio 2015 Update 3 中取得。 該選項可讓編譯器插入指示，以緩解特定的 [Spectre 安全性弱點](https://spectreattack.com/spectre.pdf)。 這些弱點稱為「*推測執行端通道」攻擊*。 它們會影響許多作業系統和現代化處理器，包括 Intel、AMD 和 ARM 的處理器。

根據預設， **/Qspectre** 選項為關閉狀態。

在其最初版本中， **/Qspectre** 選項只適用於最佳化的程式碼。 在 Visual Studio 2017 15.7 版及更新版本中， **/Qspectre** 選項可支援所有最佳化層級。

Microsoft Visual C++ 程式庫也可在具有 Spectre 風險降低功能的版本中取得。 您可以在 Visual Studio 安裝程式中，下載適用於 Visual Studio 2017 和更新版本的 Spectre 風險降低程式庫。 它們位於 [**編譯器]、[組建工具] 和 [運行**時間] 下的 [**個別元件**] 索引標籤中，並在名稱中包含 "Spectre" 程式庫。 以下 Visual C++ 執行階段的子集皆適用已啟用風險降低功能的 DLL 和靜態執行階段程式庫：VC++ 啟動程式碼、vcruntime140、msvcp140、concrt140 和 vcamp140。 僅支援應用程式本機部署的 Dll。 Visual C++ 2017 和更新版本的執行時間程式庫可轉散發套件內容尚未修改。

您也可以安裝適用于 MFC 和 ATL 的 Spectre 緩和程式庫。 它們位於 [Sdk]、[連結**庫] 和**[架構] 底下的 [**個別元件**] 索引標籤中。

> [!NOTE]
> 通用 Windows （UWP）應用程式或元件沒有 Spectre 緩和程式庫的版本。 這類程式庫的應用程式本機部署無法進行。

### <a name="applicability"></a>適用性

如果您的程式碼會在跨越信任界限的資料上運作，建議您使用 **/Qspectre**選項來重建和重新部署您的程式碼，以儘快緩和此問題。 這類程式碼的範例，就是載入不受信任的輸入可能會影響執行的程式碼。 例如，會進行遠端程序呼叫、剖析不受信任的輸入或檔案，或使用其他本機處理序間通訊（IPC）介面的程式碼。 標準沙箱技術可能不足。 請先仔細調查您的沙箱，然後再決定您的程式碼不會跨越信任界限。

### <a name="availability"></a>可用性

**/Qspectre**選項適用于 Visual Studio 2017 版本15.5.5 版，以及2018年1月23日之前C++或之後的所有 MICROSOFT 編譯器更新（MSVC）。 您可以使用 Visual Studio 安裝程式來更新編譯器，並將 Spectre 風險降低程式庫當作個別元件來安裝。 **/Qspectre** 選項也可透過修補程式在 Visual Studio 2015 Update 3 中取得。 如需詳細資訊，請參閱 [KB 4338871](https://support.microsoft.com/help/4338871)。

Visual Studio 2017 15.5 版的所有版本，以及 Visual Studio 2017 版本15.6 的所有預覽。 包含未記載的選項 **/d2guardspecload**。 它相當於 **/Qspectre**的初始行為。 您可以使用 **/d2guardspecload** 將相同風險降低功能套用到這些編譯器版本中的程式碼。 建議您更新組建，以在支援選項的編譯器中使用 **/Qspectre** 。 **/Qspectre**選項也可以支援較新版本編譯器中的新緩和措施。

### <a name="effect"></a>作用

**/Qspectre** 選項會輸出程式碼來降低 Specter 變體 1：繞過邊界檢查 ([CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)) 的風險。 其運作方式是插入作為推測式程式碼執行屏障的指示。 這些用來降低處理器推測風險的特定指示會依賴處理器和其微架構，而且可能會在未來的編譯器版本中有所變更。

當您啟用 **/Qspectre**選項時，編譯器會嘗試識別推測執行可能略過界限檢查的實例。 這就是插入屏障指示的位置。 請務必留意，編譯器可執行檔分析限制，以識別 variant 1 的實例。 因此，不保證會在 **/Qspectre**下檢測變體1的所有可能實例。

### <a name="performance-impact"></a>效能影響

在數個可調的程式碼基底中， **/Qspectre**的效能影響似乎是可忽略的。 不過，不保證 **/Qspectre**下的程式碼效能會受到影響。 您應該先制定程式碼的基準，以判斷效能選項的影響。 如果您知道效能關鍵區塊或迴圈中不需要緩和措施，您可以使用[__declspec （spectre （nomitigation））](../../cpp/spectre.md)指示詞，選擇性地停用緩和措施。 這個指示詞在僅支援 **/d2guardspecload**選項的編譯器中無法使用。

### <a name="required-libraries"></a>必要的程式庫

**/Qspectre**編譯器選項會產生程式碼，以隱含的方式連結所建立的執行時間程式庫版本，以提供 Spectre 的緩和措施。 這些程式庫都是必須使用 Visual Studio 安裝程式來安裝的選用元件：

- 適用於 Spectre \[(x86 與 x64) | (ARM) | (ARM64)] 的 MSVC *version_numbers* 版
- 適用於 \[(x86/x64) | ARM | ARM64] 的 Visual C++ ATL 與 Spectre 風險降低
- 適用於 \[x86/x64 | ARM | ARM64] 的 Visual C++ MFC 與 Spectre 風險降低

如果您使用 **/Qspectre**建立程式碼，但未安裝這些程式庫，則組建系統**會報告警告 MSB8038：已啟用 Spectre 風險降低，但找不到 Spectre 風險降低程式庫**。 如果您的 MFC 或 ATL 程式碼無法建立，而且連結器報告錯誤，例如**嚴重錯誤 LNK1104：無法開啟檔案 ' oldnames '** ，這些遺漏的程式庫可能是原因。

### <a name="additional-information"></a>其他資訊

如需詳細資訊，請參閱 < 官方的[Microsoft 資訊安全諮詢 ADV180002，以降低推測執行端通道弱點的指引](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 您可以從 Intel 的[推測性執行旁路攻擊風險降低 (Speculative Execution Side Channel Mitigations)](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 和 ARM 的[快取推測性旁路攻擊 (Cache Speculation Side-channels)](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) 中取得指導方針。 如需 Spectre 和 Meltdown 緩和措施的 Windows 特定總覽，請參閱[瞭解 Spectre 和 Meltdown 緩和措施對 Windows 系統的效能影響](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)。 如需 MSVC 緩和措施所解決之 Spectre 弱點的總覽，請參閱小組 Blog 中的C++ [SPECTRE 緩和措施 MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

::: moniker range="vs-2019"

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > ] [ **CC++ /** >程式**代碼產生**] 屬性頁。

1. 為 [ **Spectre 緩和**] 屬性選取新的值。 選擇 [確定] 以套用變更。

::: moniker-end

::: moniker range="<=vs-2017"

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [ > **C/C++**  **命令列**] 屬性頁。

1. 在 [其他選項] 方塊中輸入 **/Qspectre**編譯器選項。 選擇 [確定] 以套用變更。

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
