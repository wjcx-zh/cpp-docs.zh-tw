---
title: /Yd (將偵錯資訊置入目的檔)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: 55bb8197cd15243f65c90d7fbd2724f91fce23b4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414872"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (將偵錯資訊置入目的檔)

從先行編譯標頭 (.pch) 檔案搭配使用時建立完整的偵錯資訊置於所有目的檔的步調[/Yc](../../build/reference/yc-create-precompiled-header-file.md)並[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)選項。 已取代。

## <a name="syntax"></a>語法

```
/Yd
```

## <a name="remarks"></a>備註

**/Yd**已被取代;Visual c + + 現在支援多個物件寫入至單一的.pdb 檔案，請使用 **/Zi**改。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。

除非您要散發程式庫包含偵錯資訊，請使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項而非 **/z7**並 **/Yd**。

將完整的偵錯資訊儲存在每個.obj 檔案，則只需要將包含偵錯資訊的程式庫分散。 它會減緩編譯，而且需要大量磁碟空間。 當 **/Yc**並 **/z7**不會使用 **/Yd**，編譯器將常見的偵錯資訊儲存在從.pch 檔案建立的第一個.obj 檔案。 編譯器不會將這項資訊插入.pch 檔案，從後續建立的.obj 檔案它會插入交互參照的資訊。 無論多少的.obj 檔案使用.pch 檔案，只能有一個.obj 檔案會包含常見的偵錯資訊。

雖然此預設行為會產生更快建置時間，並減少磁碟空間需求，但也不想要如果小幅變更需要重建包含常見的偵錯資訊的.obj 檔案。 在此情況下，編譯器必須重建所有.obj 檔案包含在原始的.obj 檔案的交互參考。 此外，如果一般的.pch 檔案由不同的專案，依賴單一.obj 檔的交互參考是困難。

如需有關先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)

- [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="examples"></a>範例

假設您有兩個基底的檔案，F.cpp 和 G.cpp，每個包含這些 **#include**陳述式：

```
#include "windows.h"
#include "etc.h"
```

下列命令會建立先行編譯標頭檔案 ETC.pch 和物件檔案 F.obj:

```
CL /YcETC.H /Z7 F.CPP
```

物件檔案 F.obj 包含類型和 WINDOWS.h 和 ETC.h 的符號資訊 （以及它們所包含的任何其他標頭檔）。 現在您可以使用先行編譯標頭 ETC.pch 來編譯原始程式檔 G.cpp:

```
CL /YuETC.H /Z7 G.CPP
```

目的檔 G.obj 不包含先行編譯標頭的偵錯資訊，但只是參考 F.obj 檔案中的該資訊。 請注意，您必須使用 F.obj 檔案連結。

如果不使用先行編譯標頭 **/z7**，您仍然可以使用它在使用的更新版本編譯 **/z7**。 不過，偵錯資訊會放在目前的物件檔案中，而且函式和先行編譯標頭中所定義類型的本機符號不適用於偵錯工具。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
