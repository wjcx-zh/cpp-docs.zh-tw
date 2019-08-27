---
title: /bigobj (增加 .Obj 檔中的區段數目)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493106"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (增加 .Obj 檔中的區段數目)

**/bigobj**會增加一個物件檔案可以包含的區段數目。

## <a name="syntax"></a>語法

> **/bigobj**

## <a name="remarks"></a>備註

根據預設, 物件檔案最多可以包含 65279 (將近 2 ^ 16) 個可定址的區段。 無論指定哪一個目標平臺, 都適用此限制。 **/bigobj**會將該位址容量增加到 4294967296 (2 ^ 32)。

大部分的模組一律不會產生包含超過65279個區段的 .obj 檔案。 不過, 機器產生的程式碼, 或大量使用範本程式庫的程式碼, 可能需要可容納更多區段的 .obj 檔案。 通用 Windows 平臺 (UWP) 專案上預設會啟用 **/bigobj** , 因為電腦產生的 XAML 程式碼包含大量的標頭。 如果您在 UWP 應用程式專案上停用此選項, 程式碼可能會產生編譯器錯誤 C1128。

如需 PE-COFF 物件檔案格式的詳細資訊, 請參閱 Windows 檔中的[Pe 格式](/windows/win32/debug/pe-format)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 在 [**其他選項**] 方塊中, 輸入 **/bigobj**編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
