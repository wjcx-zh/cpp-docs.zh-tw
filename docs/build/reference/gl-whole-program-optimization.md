---
title: /GL (整個程式最佳化)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 875865a32dcb80cb8a6d8fa53646260f3d9413a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439649"
---
# <a name="gl-whole-program-optimization"></a>/GL (整個程式最佳化)

啟用整個程式最佳化。

## <a name="syntax"></a>語法

```
/GL[-]
```

## <a name="remarks"></a>備註

整個程式優化可讓編譯器以程式中所有模組的資訊執行優化。 如果沒有整個程式優化，則會針對每個模組（編譯模組）來執行優化。

整個程式優化預設為關閉，且必須明確啟用。 不過，也可以使用 **/GL-** 明確地將它停用。

透過所有模組的資訊，編譯器可以：

- 優化跨函式界限使用暫存器的功能。

- 執行追蹤全域資料修改的更好作業，讓負載和存放區的數目減少。

- 執行更好的作業來追蹤指標取值所修改的可能專案集合，減少載入和存放區的數目。

- 在模組中內嵌函式，即使函式定義于另一個模組中也一樣。

以 **/gl**產生的 .obj 檔案將無法供這類連結器公用程式使用，例如[EDITBIN](editbin-reference.md)和[DUMPBIN](dumpbin-reference.md)。

如果您使用 **/gl**和[/c](c-compile-without-linking.md)編譯您的程式，則應該使用/ltcg 連結器選項來建立輸出檔案。

[/Zi](z7-zi-zi-debug-information-format.md)無法搭配 **/gl**使用

Visual C++的後續版本可能無法讀取在目前版本中以 **/gl**產生的檔案格式。 您不應該運送包含以 **/gl**產生之 .obj 檔案的 .lib 檔案，除非您願意為所有您希望使用者使用的視覺效果C++ （現在和未來）傳送 .lib 檔案的副本。

使用 **/gl**和先行編譯標頭檔產生的 .obj 檔案不應用來建立 .lib 檔案，除非 .lib 檔案將會連結到產生 **/gl** .obj 檔案的同一部電腦上。 在連結時，將需要 .obj 檔案的先行編譯標頭檔中的資訊。

如需有關可用之優化和整個程式優化限制的詳細資訊，請參閱[/ltcg](ltcg-link-time-code-generation.md)。  **/Gl**也可以使用特性指引優化;請參閱/LTCG。  當編譯特性指引優化時，如果您想要從特性指引優化進行函式排序，您必須使用[/gy](gy-enable-function-level-linking.md)或表示/Gy. 的編譯器選項進行編譯。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 如需如何在開發環境中指定 **/gl**的詳細資訊，請參閱[/ltcg （連結時產生程式碼）](ltcg-link-time-code-generation.md) 。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
