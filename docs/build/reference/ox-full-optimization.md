---
title: '/Ox (啟用最快速的優化) '
description: MSVC/Ox 選項會將一些編譯器優化選項的速度結合成單一選項。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 10893fe1cf032f2ab56f27aa4af95b050c2ec37e
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180834"
---
# <a name="ox-enable-most-speed-optimizations"></a>`/Ox` (啟用最快速的優化) 

**`/Ox`** 編譯器選項可結合優化來加速速度。 在某些版本的 Visual Studio IDE 和編譯器說明訊息中，它稱為「*完整優化*」，但 **`/Ox`** 編譯器選項只會啟用的速度優化選項子集 **`/O2`** 。

## <a name="syntax"></a>語法

> **`/Ox`**

## <a name="remarks"></a>備註

**`/Ox`** 編譯器選項會啟用偏好 **`/O`** 速度的編譯器選項。 **`/Ox`** 編譯器選項不包含額外的[ `/GF` (消除重複字串) ](gf-eliminate-duplicate-strings.md)並[ `/Gy` (啟用功能層級連結) ](gy-enable-function-level-linking.md)啟用的選項[ `/O1` ，或 `/O2` (最小化大小，最大化速度) ](o1-o2-minimize-size-maximize-speed.md)。 和所套用的其他選項會 **`/O1`** **`/O2`** 導致字串或函式的指標共用目標位址，這可能會影響偵錯工具和嚴格的語言一致性。 **`/Ox`** 選項是在不包含和的情況下啟用大部分優化的簡單方式 **`/GF`** **`/Gy`** 。 如需詳細資訊，請參閱 [`/GF`](gf-eliminate-duplicate-strings.md) 和選項的描述 [`/Gy`](gy-enable-function-level-linking.md) 。

**`/Ox`** 編譯器選項與搭配使用下列選項的方式相同：

- [ `/Ob` (內嵌函數展開) ](ob-inline-function-expansion.md)，其中 option 參數為 2 (**`/Ob2`**) 

- [`/Oi` (產生內建函式) ](oi-generate-intrinsic-functions.md)

- [`/Ot` (偏好快速的程式碼) ](os-ot-favor-small-code-favor-fast-code.md)

- [`/Oy` (框架指標省略) ](oy-frame-pointer-omission.md)

**`/Ox`** 與互斥：

- [`/O1` (大小降) ](o1-o2-minimize-size-maximize-speed.md)

- [`/O2` (最大化速度) ](o1-o2-minimize-size-maximize-speed.md)

- [`/Od` (停用 (Debug) # B3](od-disable-debug.md)

**`/Ox`** 如果您指定 **`/Oxs`** ，這會將 **`/Ox`** 編譯器選項與[ `/Os` (偏好小型程式碼) ](os-ot-favor-small-code-favor-fast-code.md)結合，您就可以取消編譯器選項的偏向速度。 結合的選項偏好較小的程式碼大小。  **`/Oxs`** 選項與指定 **`/Ox`** **`/Os`** 選項出現在該順序中的方式完全相同。

若要將所有可用的檔案層級優化套用至發行組建，建議您指定[ `/O2` (最大化速度) ](o1-o2-minimize-size-maximize-speed.md)而不是 **`/Ox`** ，並[ `/O1` (最小化) ](o1-o2-minimize-size-maximize-speed.md) ，而不是 **`/Oxs`** 。 如需更多在發行組建中的優化功能，也請考慮[ `/GL` (整個程式優化) ](gl-whole-program-optimization.md)編譯器選項，並[ `/LTCG` (連結階段程式碼產生) ](ltcg-link-time-code-generation.md)連結器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **優化**] 屬性頁。

1. 修改**優化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A> ＞。

## <a name="see-also"></a>另請參閱

[`/O` (優化程式碼的選項) ](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
