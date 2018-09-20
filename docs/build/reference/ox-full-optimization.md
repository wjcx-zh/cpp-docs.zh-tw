---
title: -Ox （啟用大多數速度最佳化） |Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1da84c3a4ec481d3af2880a80f5923bf0c50cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438076"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox （啟用大多數速度最佳化）

**/Ox**編譯器選項可讓偏好速度的最佳化的組合。 在某些版本的 Visual Studio IDE 和編譯器說明訊息中，這稱為*完全最佳化*，但 **/Ox**編譯器選項可讓速度的最佳化選項所啟用的子集 **/O2**。

## <a name="syntax"></a>語法

> /Ox

## <a name="remarks"></a>備註

**/Ox**編譯器選項會啟用 **/O**編譯器選項的偏好速度。 **/Ox**編譯器選項不包含額外[/GF （消除重複字串）](../../build/reference/gf-eliminate-duplicate-strings.md)並[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md) 所啟用的選項[/O1 或/o2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。 所套用的其他選項 **/o1**並 **/o2**可能會導致字串或共用的目標位址，可能會影響偵錯和嚴格的語言一致性的函式的指標。 **/Ox**選項是用來啟用大多數最佳化，但不包括 **/GF**並 **/Gy**。 如需詳細資訊，請參閱的描述[/GF](../../build/reference/gf-eliminate-duplicate-strings.md)並[/Gy](../../build/reference/gy-enable-function-level-linking.md)選項。

**/Ox**編譯器選項相當於搭配使用下列選項：

- [/Ob （內嵌函式展開）](../../build/reference/ob-inline-function-expansion.md)，其中的 option 參數是 2 (**/ob2**)

- [/Og (全域最佳化)](../../build/reference/og-global-optimizations.md)

- [/Oi (產生內建函式)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot （偏好快的程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy （框架指標省略）](../../build/reference/oy-frame-pointer-omission.md)

**/Ox**是互斥的：

- [/ O1 （最小大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 （最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (停用 (偵錯))](../../build/reference/od-disable-debug.md)

您可以取消的速度偏差 **/Ox**編譯器選項，如果您指定 **/Oxs**，哪一個結合 **/Ox**編譯器選項和[（偏好小的 /Os程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。 合併的選項，而非較小的程式碼大小。

若要套用所有可用的發行組建的檔案層級最佳化，我們建議您指定[/o2 （最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)而不是 **/Ox**，並[/o1 （最小大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)改為 **/Oxs**。 在版本中的更多最佳化組建，也請考慮[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)編譯器選項和[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)連結器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 底下**組態屬性**，開啟**C/c + +** ，然後選擇**最佳化**屬性頁。

1. 修改**最佳化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)