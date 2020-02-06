---
title: /Qspectre-load
description: 描述 Microsoft C/C++編譯器（MSVC）/Qspectre-load 選項。
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load
ms.openlocfilehash: a766cf9b7eef11b7c5819cbdaa7706ab5b80c608
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035526"
---
# <a name="qspectre-load"></a>/Qspectre-load

指定編譯器產生每個載入指令的序列化指令。 此選項會擴充 **/Qspectre**旗標，以根據負載來緩和任何可能的**推測執行端通道攻擊**。

## <a name="syntax"></a>語法

> **/Qspectre-load**

## <a name="remarks"></a>備註

**/Qspectre-load**會使編譯器偵測記憶體中的負載，並在其後面插入序列化指令。 載入記憶體的控制流程指示（包括 `RET` 和 `CALL`）會分割成負載和控制流程傳輸。 負載後面接著 `LFENCE`，以確保負載受到保護。 在某些情況下，編譯器無法分割控制流程指令（例如 `jmp` 指令），因此它會使用替代的緩和技術。 例如，編譯器會藉由新增指示，在插入 LFENCE 之前先以非破壞性的方式來減輕 `jmp [rax]`，如下所示：

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

由於 **/Qspectre-load**會停止所有負載的推理，因此效能的影響很高。 緩和措施並不適合所有位置。 如果有不需要保護的效能關鍵程式碼區塊，您可以使用 `__declspec(spectre(nomitigation))`來停用這些緩和措施。 如需詳細資訊，請參閱[__declspec spectre](../../cpp/spectre.md)。

**/Qspectre-load**選項預設為關閉，並支援所有優化層級。

Visual Studio 2019 16.5 版和更新版本中提供 **/Qspectre-load**選項。 此選項只適用于以 x86 和 x64 處理器為目標的編譯器。 在以 ARM 處理器為目標的編譯器中無法使用它。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

2. 在 [ **C/C++**  > 程式**代碼產生**] 屬性頁中選取 [設定**屬性**] > 。

3. 為 [ **Spectre 緩和**] 屬性選取新的值。 選擇 [確定] 以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[/Q 選項（低層級作業）](q-options-low-level-operations.md)\
[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
