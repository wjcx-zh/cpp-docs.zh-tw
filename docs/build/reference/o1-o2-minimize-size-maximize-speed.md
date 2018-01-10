---
title: "-/O1、 /o2 （最小大小、 最快速度） |Microsoft 文件"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /o2
- /o1
dev_langs: C++
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f880b3cb806efa63299bf6cfa4aab4c72df23817
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2 (最小大小、最快速度)

選取一組預先定義會影響大小的選項和產生的程式碼的速度。

## <a name="syntax"></a>語法

> /O1  
> /O2

## <a name="remarks"></a>備註

**/O1**和**/O2**編譯器選項會設定數個特定的最佳化選項一次的快速方法。 **/O1**選項會設定個別的最佳化選項，在大多數情況下建立最小的程式碼。 **/O2**選項會設定在大多數情況下建立最快的程式碼的選項。 **/O2**選項為發行組建的預設值。 下表顯示特定的選項所設定的**/O1**和**/O2**:

|選項|相當於|
|------------|-------------------|
|**/O1** （最小大小）|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/Gs](../../build/reference/gs-control-stack-checking-calls.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/O2** （最快速度）|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/Gs](../../build/reference/gs-control-stack-checking-calls.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/O1**和**/O2**互為獨佔模式。

> [!NOTE]  
> **x86 特定**  
> 這些選項會隱含使用框架指標省略 ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) 選項。

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
[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)