---
title: /GL (整個程式最佳化)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 6251209dac74a504bb0635f0c544c39935090a42
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812378"
---
# <a name="gl-whole-program-optimization"></a>/GL (整個程式最佳化)

啟用整個程式最佳化。

## <a name="syntax"></a>語法

```
/GL[-]
```

## <a name="remarks"></a>備註

整個程式最佳化，可讓編譯器在程式中的所有模組上執行最佳化的資訊。 不需要整個程式最佳化，最佳化會對每一個模組 （編譯）。

整個程式最佳化預設為關閉，且必須明確啟用。 不過，您也可明確停用它與 **/GL-**。

使用中的所有模組的資訊，編譯器可以：

- 將暫存器的使用最佳化跨函式界限。

- 工作表現較佳的追蹤中的載入和儲存數允許減少的全域資料的修改。

- 工作表現較佳的一組可能的項目修改指標取值 （dereference），減少的數字的載入和儲存的追蹤。

- 內嵌在另一個模組中定義的函式時，即使模組中函式。

.obj 檔中產生 **/GL**將無法使用的這類連結器公用程式來[EDITBIN](editbin-reference.md)並[DUMPBIN](dumpbin-reference.md)。

如果您編譯您的程式與 **/GL**並[/c](c-compile-without-linking.md)，您應該使用 /LTCG 連結器選項來建立輸出檔。

[/ZI](z7-zi-zi-debug-information-format.md)不能搭配 **/GL**

使用產生的檔案格式 **/GL**在目前的版本中可能無法讀取由 Visual c + + 的後續版本。 您應該不寄送所產生的.obj 檔案所組成的.lib 檔案 **/GL**除非您願意寄送所有版本的 Visual c + + 的.lib 檔案的複本，否則您預期使用者現在和未來使用。

.obj 檔中產生 **/GL**建置的.lib 檔案，除非.lib 檔將會連結產生的同一部電腦上，應不到先行編譯標頭檔 **/GL** .obj 檔案。 在連結時，將會需要從.obj 檔案的先行編譯標頭檔的資訊。

如需有關可用的最佳化和整個程式最佳化限制的詳細資訊，請參閱[/LTCG](ltcg-link-time-code-generation.md)。  **/GL**也會提供特性指引的最佳化; 請參閱 /LTCG。  在編譯時的特性指引最佳化 」 和 「 如果您想要從您的特性指引最佳化的函數，您必須在以編譯[/Gy](gy-enable-function-level-linking.md)或表示 /Gy 編譯器選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 請參閱[/LTCG （連結時間程式碼產生）](ltcg-link-time-code-generation.md)如需如何指定 **/GL**開發環境中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
