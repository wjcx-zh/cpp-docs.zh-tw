---
title: /Qspectre |Microsoft Docs
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dde5d8bb2e7b973b505b467165a710546f2a6a0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716023"
---
# <a name="qspectre"></a>/Qspectre

指定編譯器產生的指示，以減少特定 Spectre 變異 1 安全性弱點。

## <a name="syntax"></a>語法

> **/Qspectre**

## <a name="remarks"></a>備註

**/Qspectre**選項是可在 Visual Studio 2017 15.7 版及更新版本。 它可讓編譯器插入減輕特定的指示[Spectre 安全性弱點](https://spectreattack.com/spectre.pdf)。 這些弱點，稱為*推測性執行旁路攻擊*、 會影響許多作業系統和現代處理器，包括 intel、 AMD 處理器和 ARM。

**/Qspectre**選項預設為關閉。

在其初始版本中， **/Qspectre**選項僅適用於最佳化程式碼。 您應該確定編譯的最佳化選項的任何程式碼 (例如[/o2 或/o1](o1-o2-minimize-size-maximize-speed.md)而非[/Od](od-disable-debug.md)) 藉此確定套用緩和措施。 同樣地，檢查 使用任何程式碼[#pragma 最佳化 (「 stg"，off)](../../preprocessor/optimize.md)。

### <a name="applicability"></a>適用性

如果您的程式碼作跨越信任界限的資料，則我們建議您改用 **/Qspectre**重建並重新部署您的程式碼，以儘速解決這個問題的選項。 跨越信任界限的資料上運作的程式碼的範例包括將不受信任的輸入可能會影響執行的程式碼、 進行遠端程序程式碼，例如，呼叫、 剖析不受信任的輸入或檔案，或使用其他區域間的程序通訊 (IPC) 的介面。 標準的沙箱技術可能不足。 在您決定您的程式碼不會跨越信任界限之前，您應該仔細調查您的沙箱。

### <a name="availability"></a>可用性

**/Qspectre**選項可用於 Visual Studio 2017 15.5.5 版和所有更新 Microsoft Visual c + + 編譯器 (MSVC) 或在 2018 年 1 月 23 日之後。 若要更新編譯器，並作為個別的元件安裝 Spectre 降低程式庫，請使用 Visual Studio 安裝程式。 **/Qspectre**選項也會適用於 Visual Studio 2015 Update 3 透過修補程式。 如需詳細資訊，請參閱 < [KB 4338871](https://support.microsoft.com/help/4338871)。

所有版本的 Visual Studio 2017 版本 15.5 版及所有預覽的 Visual Studio 15.6 版已經包含了未記載的選項， **/d2guardspecload**，它就相當於初始行為 **/Qspectre**. 您可以使用 **/d2guardspecload**到您的程式碼，在這些版本的編譯器中套用相同的緩和措施。 請更新您要使用的組建 **/Qspectre**中的支援選項，編譯器 **/Qspectre**選項也可在更新版本的編譯器支援新的緩和措施。

### <a name="effect"></a>作用

**/Qspectre**選項來降低 Specter variant 1，範圍檢查的略過的程式碼的輸出[CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)。 其運作方式插入做為推測式的程式碼執行的屏障的指示。 用來降低處理器推測的特定指示取決於處理器和其微架構，並可能會變更在未來版本的編譯器。

當 **/Qspectre**選項啟用，則編譯器會嘗試找出執行個體推測性執行可能會略過界限檢查和插入 barrier 指示的位置。 請務必請注意，有一些限制編譯器可以執行來識別變體 1 的執行個體的分析。 此情況下，則在進行檢測，variant 1 的所有可能的執行個體無法保證 **/Qspectre**。

### <a name="performance-impact"></a>效能影響

效能影響 **/Qspectre**曾予以忽略在數個非常大型的程式碼基底，但是沒有任何保證您的程式碼，在該效能 **/Qspectre**仍不會受到影響。 您應該先評定您的程式碼，以判斷效能選項的效果。 如果您知道在效能關鍵的區塊或迴圈都不需要緩和措施，緩和措施可以選擇性地停用使用[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指示詞。 這個指示詞不適用於只支援的編譯器 **/d2guardspecload**選項。

### <a name="required-libraries"></a>必要的程式庫

**/Qspectre**編譯器選項會產生隱含連結版本提供 Spectre 風險降低已建置的執行階段程式庫的程式碼。 這些程式庫都必須使用 Visual Studio 安裝程式安裝的選用元件：

- VC + + 2017年版本*version_number*用於 Spectre （x86 和 x64） 程式庫
- Visual C++ ATL (x86/x64) 與 Spectre 風險降低
- 適用於 x86/x64 的 Visual C++ MFC 與 Spectre 風險降低

如果您使用建置您的程式碼 **/Qspectre**並不是這些程式庫安裝，建置系統報告**警告 MSB8038： 已啟用 Spectre 風險降低，但找不到 spectre 風險降低程式庫**。 MFC 或 ATL 程式碼無法建置，而這類連結器回報的錯誤**嚴重錯誤 LNK1104： 無法開啟檔案 'oldnames.lib'**，這些遺漏的程式庫的可能原因。

### <a name="additional-information"></a>其他資訊

如需詳細資訊，請參閱官方[Microsoft 安全性諮詢 ADV180002、 指導方針，以減少推測性執行旁路攻擊漏洞](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 指引也會提供從 Intel[推測性執行端通道緩和措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)，和 ARM，[快取推測側邊通道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)。 Spectre 與 Meltdown 風險降低的特定 Windows 的概觀，請參閱 <<c0> [ 了解 Spectre 與 Meltdown 緩和措施，在 Windows 系統上的效能影響](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)Microsoft 安全部落格上。 如需由 MSVC 風險降低 Spectre 弱點的概觀，請參閱 < [Spectre 風險降低，在 MSVC 中的](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)Visual c + + 小組部落格上。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 請輸入 **/Qspectre**中的編譯器選項**其他選項** 方塊中。 選擇**確定**以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
