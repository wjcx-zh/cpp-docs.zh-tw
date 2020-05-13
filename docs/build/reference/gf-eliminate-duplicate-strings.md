---
title: /GF (消除重複字串)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320497"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (消除重複字串)

使編譯器能夠在執行期間在程式映射和記憶體中創建相同字串的單個副本。 這是一種稱為*字串池的*優化,可以創建較小的程式。

## <a name="syntax"></a>語法

```
/GF
```

## <a name="remarks"></a>備註

如果使用 **/GF**,操作系統不會交換記憶體的字串部分,並且可以從映射檔讀取字串。

**/GF**將字串池為唯讀字串。 如果嘗試修改 **/GF**下的字串,則會發生應用程式錯誤。

字串池允許用作多個緩衝區的多個指標作為指向單個緩衝區的多個指標。 在以下代碼中,`s`使用相同`t`的字串進行初始化。 字串池導致它們指向相同的記憶體:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> 用於編輯和繼續的[/ZI](z7-zi-zi-debug-information-format.md)選項會自動設置 **/GF**選項。

> [!NOTE]
> **/GF**編譯器選項為每個唯一字串創建一個可定址部分。 默認情況下,物件檔最多可以包含 65,536 個可定址部分。 如果程式包含超過 65,536 個字串,請使用[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)編譯器選項創建更多節。

**/GF**在使用[/O1](o1-o2-minimize-size-maximize-speed.md)或[/O2](o1-o2-minimize-size-maximize-speed.md)時生效。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 單擊 **「代碼產生」** 屬性頁。

1. 修改**啟用字串池**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
