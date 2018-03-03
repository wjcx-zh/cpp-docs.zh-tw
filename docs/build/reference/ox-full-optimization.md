---
title: "-Ox （讓大部分的速度最佳化） |Microsoft 文件"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85efa8a2beab34d0dcf1bdb74e3cf89008b10d6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox （讓大部分的速度最佳化）

**/Ox**編譯器選項可讓優先的最佳化的組合。 在某些版本的 Visual Studio IDE 和編譯器說明訊息，這稱為*完全最佳化*，但**/Ox**編譯器選項可讓速度最佳化選項，啟用的子集**/O2**。

## <a name="syntax"></a>語法

> /Ox

## <a name="remarks"></a>備註

**/Ox**編譯器選項會啟用**/O**編譯器選項，該偏好速度。 **/Ox**編譯器選項不包括額外[/GF （消除重複字串）](../../build/reference/gf-eliminate-duplicate-strings.md)和[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md) 所啟用的選項[/O1 或 /O2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。 所套用的其他選項**/O1**和**/O2**可能會導致指標字串或共用目標位址，可能會影響偵錯和嚴格一致性的函式。 **/Ox**選項是簡單的方法，但不包含啟用大部分的最佳化**/GF**和**/Gy**。 如需詳細資訊，請參閱描述[/GF](../../build/reference/gf-eliminate-duplicate-strings.md)和[/Gy](../../build/reference/gy-enable-function-level-linking.md)選項。

**/Ox**編譯器選項等同於在組合中使用下列選項：

- [/Ob （內嵌函式展開）](../../build/reference/ob-inline-function-expansion.md)，其中的 option 參數為 2 (**/Ob2**)

- [/Og （全域最佳化）](../../build/reference/og-global-optimizations.md)

- [/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot （偏好快的程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy （框架指標省略）](../../build/reference/oy-frame-pointer-omission.md)

**/Ox**從互斥：

- [/O1 （最小大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/O2 （最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od （停用 （偵錯））](../../build/reference/od-disable-debug.md)

您可以取消的速度偏差**/Ox**編譯器選項，如果您指定**/Oxs**，哪些結合**/Ox**編譯器選項搭配[/Os （偏好小程式碼）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。 合併的選項，而非較小的程式碼大小。

若要套用所有的可用檔案層級最佳化的發行組建，我們建議您指定[/O2 （最大化的速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)而不是**/Ox**，和[/O1 （最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)改為**/Oxs**。 針對組建的更多的最佳化版本中，也請考慮[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)編譯器選項和[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)連結器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 在下**組態屬性**，開啟**C/c + +** ，然後選擇 **最佳化**屬性頁。

1. 修改**最佳化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>請參閱

[/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)  
[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)