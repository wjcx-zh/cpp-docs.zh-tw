---
title: /Z7、/Zi、/ZI (偵錯資訊格式)
ms.date: 07/06/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: bc3fd9c065219a128e29290084b1e1fb51fc773e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058590"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)

**`/Z7`**、 **`/Zi`** 和 **`/ZI`** 編譯器選項會指定為您的程式建立的偵錯工具資訊類型，以及此資訊是否保留在目的檔或程式資料庫（PDB）檔案中。

## <a name="syntax"></a>語法

> **`/Z7`**\
> **`/Zi`**\
> **`/ZI`**

## <a name="remarks"></a>備註

當您指定 debug 選項時，編譯器會產生函式和變數的符號名稱、型別資訊，以及偵錯工具所使用的行位置。 這個符號偵錯工具資訊可以包含在編譯器所產生的物件檔案（檔案 *`.obj`* ）中，或是在可執行檔的個別 PDB 檔案（檔案 *`.pdb`* ）中。 下列各節將描述 debug 資訊格式選項。

### <a name="none"></a>None

根據預設，如果未指定 debug 資訊格式選項，編譯器不會產生任何偵錯工具資訊，因此編譯速度會更快。

### <a name="z7"></a>/Z7

**`/Z7`** 選項會產生物件檔案，其中也包含用於偵錯工具的完整符號調試資訊。 這些物件檔案和其所建立的任何程式庫，可能會大幅大於沒有任何偵錯工具資訊的檔案。 符號偵錯工具資訊包括變數、函式和行號的名稱和類型。 編譯器不會產生 PDB 檔案。 不過，如果已將選項傳遞給連結器，則仍然可以從這些物件檔案或程式庫產生 PDB 檔案 **`/DEBUG`** 。

針對協力廠商程式庫的 debug 版本散發者，沒有 PDB 檔案的優點。 不過，任何先行編譯標頭檔的目的檔都是程式庫連結階段和用於進行偵錯工具的必要檔案。 如果目的檔中只有類型資訊（不含程式碼） *`.pch`* ，則當您建立程式庫時，您也必須使用 [ [ `/Yl` （插入用於 Debug 程式庫的 PCH 參考](yl-inject-pch-reference-for-debug-library.md)] 選項，預設為啟用）。

當指定時，無法使用已被取代的[ `/Gm` （啟用最少重建）](gm-enable-minimal-rebuild.md)選項 **`/Z7`** 。

### <a name="zi"></a>/ZI

**`/Zi`** 選項會產生個別的 PDB 檔案，其中包含與偵錯工具搭配使用的所有符號調試資訊。 偵錯工具資訊不會包含在物件檔案或可執行檔中，這會使它們變得更小。

使用 **`/Zi`** 不會影響優化。 不過， **`/Zi`** 的確意味著 **`/debug`** 。 如需詳細資訊，請參閱[ `/DEBUG` （產生偵錯工具資訊）](debug-generate-debug-info.md)。

當您同時指定 **`/Zi`** 和時 **`/clr`** ， <xref:System.Diagnostics.DebuggableAttribute> 屬性不會放在元件中繼資料中。 如果您想要的話，您必須在原始程式碼中指定它。 這個屬性可能影響應用程式的執行階段效能。 如需 `Debuggable` 屬性如何影響效能，以及如何修改效能影響的詳細資訊，請參閱[讓影像更容易進行偵錯工具](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

編譯器會將 PDB 檔案命名為 *`<project>.pdb`* ，其中 *`<project>`* 是您的專案名稱。 如果您在專案之外編譯檔案，編譯器會建立名為的 PDB 檔案 *`VC<x>.pdb`* ，其中 *`<x>`* 是所使用之編譯器版本的主要和次要版本號碼的串連。 編譯器會在使用此選項建立的每個物件檔案中，內嵌 PDB 的名稱和識別時間戳記簽章。 這個名稱和簽章會將偵錯工具指向符號和行號資訊的位置。 PDB 檔案中的名稱和簽章必須符合要在偵錯工具中載入之符號的可執行檔。 WinDBG 偵錯工具可以使用命令來載入不相符的符號 **`.symopt+0x40`** 。 Visual Studio 沒有載入不相符符號的類似選項。

如果您從使用所編譯的物件建立程式庫 **`/Zi`** ，當程式庫連結至程式時，就必須提供相關聯的 PDB 檔案。 這表示，如果您散發程式庫，則也必須散發 PDB 檔案。 若要建立包含不使用 PDB 檔案之偵錯工具資訊的程式庫，您必須選取此 **`/Z7`** 選項。 如果您使用先行編譯標頭檔選項，先行編譯標頭和原始程式碼其餘部分的偵錯工具資訊會放在 PDB 檔案中。

### <a name="zi"></a>/ZI

**`/ZI`** 選項與類似 **`/Zi`** ，但它會以支援 [[編輯後繼續](/visualstudio/debugger/edit-and-continue-visual-cpp)] 功能的格式產生 PDB 檔案。 若要使用 [編輯後繼續] 調試功能，您必須使用此選項。 [編輯後繼續] 功能對於開發人員的生產力很有用，但可能會導致程式碼大小、效能和編譯器一致性的問題。 因為大部分的優化與 [編輯後繼續] 不相容，所以使用會 **`/ZI`** 停用 `#pragma optimize` 程式碼中的任何語句。 **`/ZI`** 選項也與使用[ `__LINE__` 預先定義的宏](../../preprocessor/predefined-macros.md)不相容; 使用編譯的程式碼 **`/ZI`** 不能當做 `__LINE__` 非類型樣板引數使用，雖然 `__LINE__` 可以在宏擴充中使用。

**`/ZI`** 選項會強制在編譯中使用[ `/Gy` （[啟用函式層級連結]）](gy-enable-function-level-linking.md)和 [ [ `/FC` （診斷中的原始程式碼檔的完整路徑）](fc-full-path-of-source-code-file-in-diagnostics.md) ] 選項。

**`/ZI`** 與[ `/clr` （Common Language Runtime 編譯）](clr-common-language-runtime-compilation.md)不相容。

> [!NOTE]
> 此 **`/ZI`** 選項僅適用于以 x86 和 x64 處理器為目標的編譯器。 以 ARM 處理器為目標的編譯器無法使用此編譯器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] [  >  **c/c + +**  >  **一般**] 屬性頁。

1. 修改 [**調試資訊格式**] 屬性。 選取 [確定]**** 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
