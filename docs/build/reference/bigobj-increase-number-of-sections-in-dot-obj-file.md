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
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272971"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (增加 .Obj 檔中的區段數目)

**/bigobj**會增加物件檔案可以包含的區段數目。

## <a name="syntax"></a>語法

> **/bigobj**

## <a name="remarks"></a>備註

根據預設，物件檔案可以保存多達 65,279 (幾乎 2 ^16) 可定址區段。 這項限制適用於指定不論哪一個目標平台。 **/bigobj**增加 4294967296 該位址容量 (2 ^32)。

大部分的模組永遠不會產生包含多個 65279 個區段的.obj 檔案。 不過，機器產生的程式碼或大量使用範本程式庫的程式碼可能需要可以保存多個區段的.obj 檔案。 **/bigobj**因為機器產生的 XAML 程式碼包含大量標頭的通用 Windows 平台 (UWP) 專案的預設會啟用。 如果您停用此選項在 UWP 應用程式專案，您的程式碼可能會產生編譯器錯誤 C1128。

如需 PE COFF 物件檔案格式資訊，請參閱[PE 格式](/windows/desktop/debug/pe-format)Windows 文件中。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **命令列**屬性頁。

1. 請輸入 **/bigobj**中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
