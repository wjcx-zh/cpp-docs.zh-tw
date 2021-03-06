---
title: /FA、/Fa (清單檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
ms.openlocfilehash: b78704ea12365d9e10222d75c6807517f7cdb893
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292831"
---
# <a name="fa-fa-listing-file"></a>/FA、/Fa (清單檔)

建立清單檔包含組譯工具程式碼。

## <a name="syntax"></a>語法

> **/FA**[**c**\][**s**\][**u**] **/Fa**_pathname_

## <a name="remarks"></a>備註

**/FA**編譯器選項產生的組譯工具清單檔案中每個轉譯單位是編譯，通常會對應至 C 或C++原始程式檔。 根據預設，只有組譯工具包含在清單檔案中，會編碼為 ANSI。 選擇性**c**， **s**，並**u**引數 **/FA**控制項是否機器的程式碼或原始程式碼以及組譯工具輸出列出方式，以及是否清單會編碼為 utf-8。

根據預設，每個清單檔案取得相同的基底名稱為原始程式檔中，且.asm 延伸模組。 當機器的程式碼使用包含**c**選項時，清單檔的副檔名為.cod。 您可以變更的名稱和副檔名的清單檔並建立使用所在之目錄 **/Fa**選項。

### <a name="fa-arguments"></a>/FA 引數

none<br/>
只有組合器語言包含在清單中。

**C**<br/>
選擇性。 在清單中包含機器的程式碼。

**s**<br/>
選擇性。 包含在清單中的原始程式碼。

**u**<br/>
選擇性。 將清單檔案，以 utf-8 格式編碼，並包含位元組順序標記。 根據預設，檔案被編碼為 ANSI。 使用`u`建立清單檔，會正確顯示在任何系統上，或如果您使用 Unicode 原始程式碼檔做為編譯器的輸入。

如果兩個**s**並**u**指定，而且如果原始程式碼檔使用 Unicode 編碼方式，除了 utf-8，則程式碼中的程式行會.asm 檔可能無法正確顯示。

### <a name="fa-argument"></a>/Fa 引數

none<br/>
一*來源*.asm 檔建立的編譯過程中每個原始程式碼檔案。

*filename*<br/>
清單檔名為*filename*.asm 會置於目前的目錄。 編譯單一原始程式碼檔案時，這是才有效。

*filename.extension*<br/>
清單檔名為*filename.extension*放在目前的目錄。 編譯單一原始程式碼檔案時，這是才有效。

*directory*__\\__<br/>
一*source_file*.asm 檔會建立並放置在指定*directory*的編譯過程中每個原始程式碼檔案。 請注意所需的尾端有反斜線。 允許只在目前的磁碟上的路徑。

*directory*__\\__*filename*<br/>
清單檔名為*檔名*.asm 會置於指定*directory*。 編譯單一原始程式碼檔案時，這是才有效。

*directory*__\\__*filename.extension*<br/>
清單檔名為*filename.extension*放在指定*directory*。 編譯單一原始程式碼檔案時，這是才有效。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **輸出檔**屬性頁。

1. 修改**組合語言輸出**屬性來設定 **/FAc**並 **/FAs**組譯工具、 機器和原始碼的選項。 修改**使用 Unicode 的組譯工具清單**屬性來設定 **/FAu** ANSI 或 utf-8 輸出的選項。 修改**ASM 清單位置**來設定 **/Fa**以列出檔案名稱和位置的選項。

請注意，將兩者**組合語言輸出**並**使用 Unicode 的組譯工具清單**屬性可能會導致[命令列警告 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)。 若要結合這些選項在 IDE 中的，使用**其他選項**欄位中**命令列**屬性改為頁面。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。 若要指定 **/FAu**，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="example"></a>範例

下列命令列會產生合併的來源和機器程式碼清單稱為 HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
