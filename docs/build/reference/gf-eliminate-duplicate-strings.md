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
ms.openlocfilehash: 90d3fb5c601d9534215a46594884be5d168fe0aa
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449539"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (消除重複字串)

可讓編譯器在執行期間在程式映像和記憶體中建立一份完全相同的字串。 這是呼叫最佳化*字串共用*，可以建立較小的程式。

## <a name="syntax"></a>語法

```
/GF
```

## <a name="remarks"></a>備註

如果您使用 **/GF**，作業系統不會交換記憶體的字串部分，並可以讀取字串後，從映像檔。

**/GF**集區為唯讀的字串。 如果您嘗試修改字串底下 **/GF**，應用程式錯誤，就會發生。

字串共用，可讓項目做為多個緩衝區的多個指標是多個單一緩衝區的指標。 下列程式碼中，`s`和`t`以相同的字串初始化。 字串共用，使其指向相同的記憶體：

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  [/ZI](z7-zi-zi-debug-information-format.md)選項，用於編輯後繼續，會自動設定 **/GF**選項。

> [!NOTE]
>  **/GF**編譯器選項會建立每個唯一字串的可定址區段。 而根據預設，物件檔案可以包含最多 65,536 個可定址的區段。 如果您的程式包含超過 65536 的字串，使用[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)編譯器選項，來建立更多區段。

**/GF**是何時生效[/o1](o1-o2-minimize-size-maximize-speed.md)或是[/o2](o1-o2-minimize-size-maximize-speed.md)用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改**啟用字串共用**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
