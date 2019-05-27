---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e44416a44a9f772c17bc734d26c62ff87be775c8
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837410"
---
# <a name="qspectre"></a>/Qspectre

指定產生指示的編譯器，以減少特定 Spectre 變體 1 的安全性弱點。

## <a name="syntax"></a>語法

> **/Qspectre**

## <a name="remarks"></a>備註

**/Qspectre** 選項已在 Visual Studio 2017 15.5.5 版和更新版本中提供，也可透過 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre) 在 Visual Studio 2015 Update 3 中取得。 該選項可讓編譯器插入指示，以緩解特定的 [Spectre 安全性弱點](https://spectreattack.com/spectre.pdf)。 這些稱為「推測性執行旁路攻擊」的弱點會影響許多作業系統和新式處理器，包括 Intel、AMD 和 ARM。

根據預設，**/Qspectre** 選項為關閉狀態。

在其最初版本中，**/Qspectre** 選項只適用於最佳化的程式碼。 在 Visual Studio 2017 15.7 版及更新版本中，**/Qspectre** 選項可支援所有最佳化層級。

Microsoft Visual C++ 程式庫也可在具有 Spectre 風險降低功能的版本中取得。 您可以在 Visual Studio 安裝程式中，下載適用於 Visual Studio 2017 和更新版本的 Spectre 風險降低程式庫。 您可以在 [編譯器、建置工具與執行階段] 底下的 [個別元件] 索引標籤中，找到這些名稱中有 "Libs for Spectre" 的程式庫。 以下 Visual C++ 執行階段的子集皆適用已啟用風險降低功能的 DLL 和靜態執行階段程式庫：VC++ 啟動程式碼、vcruntime140、msvcp140、concrt140 和 vcamp140。 DLL 僅適用於應用程式本機部署；我們尚未修改 Visual C++ 2017 版或更新版「執行階段程式庫可轉散發套件」的內容。 您也可以安裝適用於 MFC 和 ATL 的 Spectre 風險降低程式庫，其位於 [SDK、程式庫和架構] 底下的 [個別元件] 索引標籤中。

### <a name="applicability"></a>適用性

如果程式碼在跨越信任界限的資料上運作，我們建議您使用 **/Qspectre** 選項來重建及重新部署您的程式碼，以儘速解決此問題。 在跨越信任界限資料上運作的程式碼範例包括：會載入不受信任輸入而影響執行的程式碼，例如進行遠端程序呼叫程、剖析不受信任輸入或檔案，或使用其他區域內含式通訊 (IPC) 介面的程式碼。 標準沙箱技術可能不足。 在您決定不讓程式碼跨越信任界限之前，應該仔細檢查您的沙箱。

### <a name="availability"></a>可用性

**/Qspectre** 選項適用於 Visual Studio 2017 15.5.5 版，以及所有在 2018 年 1 月 23 日 (或之後) 完成的 Microsoft MSVC 編譯器 (MSVC) 更新。 您可以使用 Visual Studio 安裝程式來更新編譯器，並將 Spectre 風險降低程式庫當作個別元件來安裝。 **/Qspectre** 選項也可透過修補程式在 Visual Studio 2015 Update 3 中取得。 如需詳細資訊，請參閱 [KB 4338871](https://support.microsoft.com/help/4338871)。

所有 Visual Studio 2017 15.5 版及 Visual Studio 2017 15.6 預覽版都包含了未記載的選項：**/d2guardspecload**，其相當於 **/Qspectre** 的初始行為。 您可以使用 **/d2guardspecload** 將相同風險降低功能套用到這些編譯器版本中的程式碼。 請更新您的組建，以在支援該選項的編譯器中使用 **/Qspectre**；**/Qspectre** 選項也會在未來的編譯器版本中支援新的風險降低功能。

### <a name="effect"></a>作用

**/Qspectre** 選項會輸出程式碼來降低 Specter 變體 1：繞過邊界檢查 ([CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)) 的風險。 其運作方式是插入作為推測式程式碼執行屏障的指示。 這些用來降低處理器推測風險的特定指示會依賴處理器和其微架構，而且可能會在未來的編譯器版本中有所變更。

當 **/Qspectre** 選項啟用時，編譯器會嘗試識別其中推測性執行可能略過邊界檢查的執行個體，然後插入屏障指示。 請務必注意，編譯器在執行分析來識別變體 1 執行個體時會有一些限制。 因此，不能保證 **/Qspectre** 能檢測到所有可能的變體 1 執行個體。

### <a name="performance-impact"></a>效能影響

**/Qspectre** 的效能影響已在數個非常大型的程式碼基底中予以忽略，但是無法保證 **/Qspectre** 底下的程式碼效能仍不受影響。 您應該先制定程式碼的基準，以判斷效能選項的影響。 如果您知道效能關鍵區塊或迴圈都不需要風險降低功能，則可以選擇性地使用 [__declspec(spectre(nomitigation))](../../cpp/spectre.md) 指示詞來停用風險降低功能。 這個指示詞不適用於只支援 **/d2guardspecload** 選項的編譯器。

### <a name="required-libraries"></a>必要的程式庫

**/Qspectre** 編譯器選項會產生程式碼，以隱含地連結到為提供 Spectre 風險降低功能而建置的執行階段程式庫版本。 這些程式庫都是必須使用 Visual Studio 安裝程式來安裝的選用元件：

- 適用於 Spectre \[(x86 與 x64) | (ARM) | (ARM64)] 的 MSVC *version_numbers* 版
- 適用於 \[(x86/x64) | ARM | ARM64] 的 Visual C++ ATL 與 Spectre 風險降低
- 適用於 \[x86/x64 | ARM | ARM64] 的 Visual C++ MFC 與 Spectre 風險降低

如果您使用 **/Qspectre** 來建置您的程式碼，但未安裝這些程式庫，則建置系統會回報**警告 MSB8038：已啟用 Spectre 風險降低，但找不到 Spectre 風險降低程式庫**。 如果 MFC 或 ATL 程式碼無法建置，則連結器會回報類似**嚴重錯誤 LNK1104：無法開啟檔案 'oldnames.lib'** 的錯誤，而這些遺漏的程式庫可能就是原因。

### <a name="additional-information"></a>其他資訊

如需詳細資訊，請參閱官方的 [Microsoft 資訊安全諮詢 ADV180002：因應推測性執行旁路攻擊弱點的指導方針](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 您可以從 Intel 的[推測性執行旁路攻擊風險降低 (Speculative Execution Side Channel Mitigations)](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 和 ARM 的[快取推測性旁路攻擊 (Cache Speculation Side-channels)](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) 中取得指導方針。 如需 Windows 專屬的 Spectre 和 Meltdown 風險降低概觀，請在 Microsoft Secure 部落格上參閱[了解 Windows 系統上 Spectre 和 Meltdown 風險降低的效能影響](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)。 如需由 MSVC 風險降低措施解決的 Spectre 弱點概觀，請在 Visual C++ Team Blog 上參閱 [MSVC 中的 Spectre 風險降低措施](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 在 [其他選項] 方塊中輸入 **/Qspectre**編譯器選項。 選擇 [確定] 以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
