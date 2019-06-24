---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e0d3af50015b77af297cbee22f439cd17d803de9
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344155"
---
# <a name="qspectre"></a>/Qspectre

指定產生指示的編譯器，以減少特定 Spectre 變體 1 的安全性弱點。

## <a name="syntax"></a>語法

> **/Qspectre**

## <a name="remarks"></a>備註

**/Qspectre** 選項已在 Visual Studio 2017 15.5.5 版和更新版本中提供，也可透過 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre) 在 Visual Studio 2015 Update 3 中取得。 該選項可讓編譯器插入指示，以緩解特定的 [Spectre 安全性弱點](https://spectreattack.com/spectre.pdf)。 會呼叫這些弱點*推測性執行旁路攻擊*。 它們會影響許多作業系統和現代處理器，包括 Intel、 AMD 和 ARM 處理器。

根據預設， **/Qspectre** 選項為關閉狀態。

在其最初版本中， **/Qspectre** 選項只適用於最佳化的程式碼。 在 Visual Studio 2017 15.7 版及更新版本中， **/Qspectre** 選項可支援所有最佳化層級。

Microsoft Visual C++ 程式庫也可在具有 Spectre 風險降低功能的版本中取得。 您可以在 Visual Studio 安裝程式中，下載適用於 Visual Studio 2017 和更新版本的 Spectre 風險降低程式庫。 它們位於**個別元件**索引標籤下**編譯器、 建置工具和執行階段**，並在名稱中有 「 程式庫的 Spectre"。 以下 Visual C++ 執行階段的子集皆適用已啟用風險降低功能的 DLL 和靜態執行階段程式庫：VC++ 啟動程式碼、vcruntime140、msvcp140、concrt140 和 vcamp140。 應用程式本機部署只支援 Dll。 視覺效果的內容C++2017年和更新版本執行階段程式庫可轉散發套件尚未被修改。

您也可以安裝 Spectre 降低程式庫的 MFC 和 ATL 它們位於**個別元件**索引標籤下**Sdk、 程式庫和架構**。

### <a name="applicability"></a>適用性

如果您的程式碼操作資料，跨越信任界限，則我們建議您改用 **/Qspectre**重建並重新部署您的程式碼，以儘速解決這個問題的選項。 這類程式碼範例是將不受信任的輸入可能會影響執行的程式碼。 比方說，讓遠端程序的程式碼會呼叫、 剖析不受信任的輸入或檔案，或使用其他的本機處理序間通訊 (IPC) 介面。 標準沙箱技術可能不足。 在您決定您的程式碼不會跨信任界限之前，仔細調查您的沙箱。

### <a name="availability"></a>可用性

**/Qspectre**選項是適用於 Visual Studio 2017 15.5.5，版中，以及 Microsoft 的所有更新C++或 2018 年 1 月 23 日之後的編譯器 (MSVC)。 您可以使用 Visual Studio 安裝程式來更新編譯器，並將 Spectre 風險降低程式庫當作個別元件來安裝。 **/Qspectre** 選項也可透過修補程式在 Visual Studio 2015 Update 3 中取得。 如需詳細資訊，請參閱 [KB 4338871](https://support.microsoft.com/help/4338871)。

和所有版本的 Visual Studio 2017 15.5 版中，所有預覽的 Visual Studio 2017 15.6 版。 包含未記載的選項， **/d2guardspecload**。 它相當於初始的行為 **/Qspectre**。 您可以使用 **/d2guardspecload** 將相同風險降低功能套用到這些編譯器版本中的程式碼。 我們建議您更新您要使用的組建 **/Qspectre**支援選項的編譯器中。 **/Qspectre**選項也可在更新版本的編譯器支援新的緩和措施。

### <a name="effect"></a>作用

**/Qspectre** 選項會輸出程式碼來降低 Specter 變體 1：繞過邊界檢查 ([CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)) 的風險。 其運作方式是插入作為推測式程式碼執行屏障的指示。 這些用來降低處理器推測風險的特定指示會依賴處理器和其微架構，而且可能會在未來的編譯器版本中有所變更。

當您啟用 **/Qspectre**選項，編譯器會嘗試識別執行個體推測性執行可能會略過界限檢查。 這就是它會插入 barrier 指示。 請務必要注意的限制與分析，編譯器可以用於識別變體 1 的執行個體。 此情況下，則在進行檢測，variant 1 的所有可能的執行個體無法保證 **/Qspectre**。

### <a name="performance-impact"></a>效能影響

效能影響 **/Qspectre**似乎就可以忽略在數個可調整大小的程式碼基底。 不過，沒有任何保證效能的程式碼底下 **/Qspectre**仍不會受到影響。 您應該先制定程式碼的基準，以判斷效能選項的影響。 如果您知道緩和措施不需要在效能關鍵的區塊或迴圈中，您可以選擇性地停用緩和措施善用[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指示詞。 這個指示詞不適用於只支援的編譯器 **/d2guardspecload**選項。

### <a name="required-libraries"></a>必要的程式庫

**/Qspectre**編譯器選項會產生隱含連結版本建置，以提供 Spectre 風險降低的執行階段程式庫的程式碼。 這些程式庫都是必須使用 Visual Studio 安裝程式來安裝的選用元件：

- 適用於 Spectre \[(x86 與 x64) | (ARM) | (ARM64)] 的 MSVC *version_numbers* 版
- 適用於 \[(x86/x64) | ARM | ARM64] 的 Visual C++ ATL 與 Spectre 風險降低
- 適用於 \[x86/x64 | ARM | ARM64] 的 Visual C++ MFC 與 Spectre 風險降低

如果您使用建置您的程式碼 **/Qspectre**與這些程式庫未安裝，建置系統報告**警告 MSB8038:已啟用 Spectre 風險降低，但找不到 Spectre 風險降低程式庫**。 如果 MFC 或 ATL 程式碼無法建置，而且這類連結器回報的錯誤**嚴重錯誤 LNK1104： 無法開啟檔案 'oldnames.lib'** ，這些遺漏的程式庫的可能原因。

### <a name="additional-information"></a>其他資訊

如需詳細資訊，請參閱官方[Microsoft 安全性諮詢 ADV180002、 指導方針，以減少推測性執行旁路攻擊漏洞](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 您可以從 Intel 的[推測性執行旁路攻擊風險降低 (Speculative Execution Side Channel Mitigations)](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 和 ARM 的[快取推測性旁路攻擊 (Cache Speculation Side-channels)](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) 中取得指導方針。 Spectre 與 Meltdown 風險降低的特定 Windows 的概觀，請參閱 <<c0> [ 了解 Spectre 與 Meltdown 緩和措施，在 Windows 系統上的效能影響](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)。 如需定址 MSVC 風險降低 Spectre 弱點的概觀，請參閱[Spectre 風險降低，在 MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./)上C++小組部落格。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性]   > [C/C++]   > [命令列]  屬性頁。

1. 在 [其他選項]  方塊中輸入 **/Qspectre**編譯器選項。 選擇 [確定]  以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
