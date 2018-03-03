---
title: "/ Qspectre |Microsoft 文件"
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b114239ad57b484c9290fbe1cc2f0ae18cb565ec
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="qspectre"></a>/Qspectre

指定編譯器產生的指示，以減少特定 Spectre variant 1 安全性弱點。

## <a name="syntax"></a>語法

> **/Qspectre**

## <a name="remarks"></a>備註

**/Qspectre**選項會使編譯器插入緩和特定指示[Spectre 安全性弱點](https://spectreattack.com/spectre.pdf)。 這些弱點，稱為*推測執行側邊通道攻擊*、 會影響許多作業系統和現代處理器，包括 Intel、 AMD 處理器和 ARM。

**/Qspectre**選項預設為關閉。

在初始的版本中， **/Qspectre**選項只適用於最佳化程式碼。 您應該確定使用的任何最佳化選項編譯程式碼 (例如， [/O2 或 /O1](o1-o2-minimize-size-maximize-speed.md)但不是[/Od](od-disable-debug.md)) 以確定會套用緩和措施。 同樣地，檢查使用的任何程式碼[#pragma 最佳化 (「 stg"，off)](../../preprocessor/optimize.md)。

### <a name="applicability"></a>適用性

如果您的程式碼操作跨越信任界限的資料，則我們建議您改用**/Qspectre**選項來重建並重新部署您的程式碼，以儘速減輕這個問題。 跨越信任界限的資料上運作的程式碼的範例包括載入未受信任的輸入可能會影響執行的程式碼，進行遠端程序的程式碼，例如呼叫、 剖析不受信任的輸入或檔案，或使用其他本機的內部處理序通訊 (IPC) 介面。 標準的沙箱技術可能不足。 在您決定您的程式碼並不會跨越信任界限之前，您應該仔細調查您沙箱。

### <a name="availability"></a>可用性

**/Qspectre**選項位於 Visual Studio 2017 版本 15.5.5 和進行當天或之後 2018 年 1 月 23，Microsoft Visual c + + 編譯器 (MSVC) 的所有更新。

所有版本的 Visual Studio 2017 版本 15.5 」 和 「 全部預覽 Visual Studio 版本的 15.6 已包含未記載的選項， **/d2guardspecload**，也就是對等項目初始的行為**/Qspectre**. 您可以使用**/d2guardspecload**来套用至這些版本的編譯器中程式碼相同的防護措施。 請更新您的組建使用**/Qspectre**支援選項; 的編譯器中**/Qspectre**選項也可以在更新版本的編譯器支援新的防護措施。

### <a name="effect"></a>作用

**/Qspectre**選項輸出程式碼，以減輕 Specter variant 1，範圍檢查的略過[CVE-2017年-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)。 其運作方式是插入做為推測性程式碼執行屏障的指示。 可用來降低處理器推測的特定指示取決於處理器，而其微架構，也可能在未來變更版本的編譯器。

當**/Qspectre**啟用選項，編譯器會嘗試識別推測執行可能會略過界限檢查，會插入屏障指令的執行個體。 請務必注意有限制，以識別 variant 1 的執行個體時編譯器可執行的分析。 因此，建議您 variant 1 的所有可能的執行個體已執行檢測下不保證**/Qspectre**。

### <a name="performance-impact"></a>效能的影響

效能影響**/Qspectre**曾予以忽略在數個非常大的程式碼基底，但是沒有任何保證待測程式碼的效能**/Qspectre**仍不會受到影響。 您應該基準測試您的程式碼，以判斷效能選項的效果。 如果您知道在效能關鍵的區塊或迴圈中並不需要緩和措施，緩和措施可以選擇性地停用使用[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指示詞。 這個指示詞不適用於只支援的編譯器**/d2guardspecload**選項。

### <a name="additional-information"></a>其他資訊

如需詳細資訊，請參閱正式[Microsoft 安全性摘要報告 ADV180002、 指引減輕推測執行側邊通道弱點](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 指引也會提供 intel[推測執行側邊通道緩和措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)，和 ARM[快取推測側邊通道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)。 Spectre 與溶解安全防護功能的特定 Windows 的概觀，請參閱[了解 Spectre 和溶解防護功能，在 Windows 系統上的效能影響](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)Microsoft 安全部落格上。 如需 Spectre 弱點定址 MSVC 防護功能的概觀，請參閱[Spectre 緩和措施 MSVC 中的](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)Visual c + + 團隊部落格上。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 輸入**/Qspectre**編譯器選項在**其他選項**方塊。 選擇**確定**以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](../../build/reference/q-options-low-level-operations.md)  
[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
