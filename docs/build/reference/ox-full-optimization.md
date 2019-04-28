---
title: /Ox （啟用大多數速度最佳化）
ms.date: 10/18/2018
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
ms.openlocfilehash: e39905608087425fe5a445f4ef88434d73bb2ded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320093"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox （啟用大多數速度最佳化）

**/Ox**編譯器選項可讓偏好速度的最佳化的組合。 在某些版本的 Visual Studio IDE 和編譯器說明訊息中，這稱為*完全最佳化*，但 **/Ox**編譯器選項可讓速度的最佳化選項所啟用的子集 **/O2**。

## <a name="syntax"></a>語法

> **/Ox**

## <a name="remarks"></a>備註

**/Ox**編譯器選項會啟用 **/O**編譯器選項的偏好速度。 **/Ox**編譯器選項不包含額外[/GF （消除重複字串）](gf-eliminate-duplicate-strings.md)並[/Gy （啟用函式階層連結）](gy-enable-function-level-linking.md) 所啟用的選項[/O1 或/o2 （最小大小、 最快速度）](o1-o2-minimize-size-maximize-speed.md)。 所套用的其他選項 **/o1**並 **/o2**可能會導致字串或共用的目標位址，可能會影響偵錯和嚴格的語言一致性的函式的指標。 **/Ox**選項是用來啟用大多數最佳化，但不包括 **/GF**並 **/Gy**。 如需詳細資訊，請參閱的描述[/GF](gf-eliminate-duplicate-strings.md)並[/Gy](gy-enable-function-level-linking.md)選項。

**/Ox**編譯器選項相當於搭配使用下列選項：

- [/Ob （內嵌函式展開）](ob-inline-function-expansion.md)，其中的 option 參數是 2 (**/ob2**)

- [/Og (全域最佳化)](og-global-optimizations.md)

- [/Oi (產生內建函式)](oi-generate-intrinsic-functions.md)

- [/Ot （偏好快的程式碼）](os-ot-favor-small-code-favor-fast-code.md)

- [/Oy （框架指標省略）](oy-frame-pointer-omission.md)

**/Ox**是互斥的：

- [/ O1 （最小大小）](o1-o2-minimize-size-maximize-speed.md)

- [/ O2 （最快速度）](o1-o2-minimize-size-maximize-speed.md)

- [/Od (停用 (偵錯))](od-disable-debug.md)

您可以取消的速度偏差 **/Ox**編譯器選項，如果您指定 **/Oxs**，哪一個結合 **/Ox**編譯器選項和[（偏好小的 /Os程式碼）](os-ot-favor-small-code-favor-fast-code.md)。 合併的選項，而非較小的程式碼大小。  **/Oxs**選項是完全如同指定 **/Ox** **/Os**時的選項會顯示依此順序。

若要套用所有可用的發行組建的檔案層級最佳化，我們建議您指定[/o2 （最快速度）](o1-o2-minimize-size-maximize-speed.md)而不是 **/Ox**，並[/o1 （最小大小）](o1-o2-minimize-size-maximize-speed.md)改為 **/Oxs**。 在版本中的更多最佳化組建，也請考慮[/GL （整個程式最佳化）](gl-whole-program-optimization.md)編譯器選項和[/LTCG （連結時間程式碼產生）](ltcg-link-time-code-generation.md)連結器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 底下**組態屬性**，開啟**C /C++**  ，然後選擇 [**最佳化**] 屬性頁。

1. 修改**最佳化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
