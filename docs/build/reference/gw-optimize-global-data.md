---
title: /Gw (最佳化全域資料)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 8afdb21defbbc8309b27749ab18a40f9555139e5
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450131"
---
# <a name="gw-optimize-global-data"></a>/Gw (最佳化全域資料)

將全域資料封裝在 COMDAT 區段中以進行最佳化。

## <a name="syntax"></a>語法

```
/Gw[-]
```

## <a name="remarks"></a>備註

**/Gw**選項可讓編譯器將全域資料封裝在個別的 COMDAT 區段中。 根據預設， **/Gw**已關閉，而且您必須明確啟用。 若要明確停用，請使用 **/Gw-** 。 當兩者 **/Gw**並[/GL](gl-whole-program-optimization.md)會啟用，連結器會使用整個程式最佳化多個目的檔比較 COMDAT 區段，以排除未參考的全域資料，或合併相同唯讀全域資料。 這可以大幅減小產生的二進位可執行檔之大小。

當您編譯和連結分別時，您可以使用[/opt: ref](opt-optimizations.md)排除未參考的全域資料，在物件檔編譯可執行檔的連結器選項 **/Gw**選項。

您也可以使用[/opt: icf](opt-optimizations.md)並[/LTCG](ltcg-link-time-code-generation.md)在一起，以合併多個目的檔任何相同唯讀全域資料編譯可執行檔中的連結器選項 **/Gw**選項。

如需詳細資訊，請參閱 <<c0> [ 簡介 /Gw 編譯器參數](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/)在C++團隊部落格。</c0>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取  **C /C++** 資料夾。

1. 選取 **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Gw** ，然後選擇**確定**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
