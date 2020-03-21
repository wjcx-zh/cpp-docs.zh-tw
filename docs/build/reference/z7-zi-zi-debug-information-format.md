---
title: /Z7、/Zi、/ZI (偵錯資訊格式)
ms.date: 04/08/2019
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
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078256"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)

指定針對程式所建立的偵錯工具資訊類型，以及此資訊是保留在物件檔案或程式資料庫（PDB）檔案中。

## <a name="syntax"></a>語法

> **/Z**{**7**|**我**|**i**}

## <a name="remarks"></a>備註

當程式碼經過編譯並以 debug 模式建立時，編譯器會為函式和變數、型別資訊和行號位置產生符號名稱，供偵錯工具使用。 這個符號偵錯工具資訊可以包含在編譯器所產生的物件檔案（.obj 檔案）中，或是在可執行檔的個別 PDB 檔案（.pdb 檔案）中。  下列各節將描述 debug 資訊格式選項。

### <a name="none"></a>None

根據預設，如果未指定 debug 資訊格式選項，編譯器不會產生任何偵錯工具資訊，因此編譯速度會更快。

### <a name="z7"></a>/Z7

**/Z7**選項會產生物件檔案，其中也包含用於偵錯工具的完整符號調試資訊。 這些物件檔案和建立的可執行檔可以大幅大於沒有任何偵錯工具資訊的檔案。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。 不會產生 PDB 檔案。

針對協力廠商程式庫的 debug 版本散發者，沒有 PDB 檔案的優點。 不過，任何先行編譯標頭檔的目的檔都是程式庫連結階段和用於進行偵錯工具的必要檔案。 如果 .pch 物件檔案中只有類型資訊（而沒有程式碼），您也必須使用[/Yl （插入 Pch Reference For Debug Library）](yl-inject-pch-reference-for-debug-library.md)選項，這在您建立程式庫時預設為啟用。

當指定 **/Z7**時，無法使用已被取代的[/Gm （啟用最少重建）](gm-enable-minimal-rebuild.md)選項。

### <a name="zi"></a>/ZI

**/Zi**選項會產生個別的 PDB 檔案，其中包含與偵錯工具搭配使用的所有符號調試資訊。 偵錯工具資訊不會包含在目的檔或可執行檔中，這會使它們變得更小。

使用 **/zi**並不會影響優化。 不過， **/zi**的確代表 **/debug**;如需詳細資訊，請參閱[/debug （產生偵錯工具資訊）](debug-generate-debug-info.md) 。

當您同時指定 **/zi**和 **/clr**時，<xref:System.Diagnostics.DebuggableAttribute> 屬性不會放在元件中繼資料中。 如果您想要的話，您必須在原始程式碼中指定它。 這個屬性可能影響應用程式的執行階段效能。 如需有關可**調試**屬性如何影響效能，以及如何修改效能影響的詳細資訊，請參閱[讓影像更容易進行偵錯工具](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

編譯器會將 PDB 檔案的*專案*命名為 .pdb。 如果您在專案之外編譯檔案，編譯器會建立一個名為 VC*x*.PDB 的 pdb 檔案，其中*x*是所使用之編譯器版本的主要和次要版本號碼的串連。 編譯器會在使用這個選項建立的每個物件檔案中內嵌 PDB 的名稱和識別時間戳記簽章，這會將偵錯工具指向符號和行號資訊的位置。 PDB 檔案中的名稱和簽章必須符合要在偵錯工具中載入之符號的可執行檔。 WinDBG 偵錯工具可以使用 `.symopt+0x40` 命令來載入不相符的符號。 Visual Studio 沒有載入不相符符號的類似選項。

如果您從使用 **/zi**編譯的物件建立程式庫，則當程式庫連結至程式時，必須要有相關聯的 .pdb 檔案。 因此，如果您散發程式庫，則也必須散發 PDB 檔案。 若要建立包含不使用 PDB 檔案之偵錯工具資訊的程式庫，您必須選取 [ **/Z7** ] 選項。 如果您使用先行編譯標頭檔選項，先行編譯標頭和原始程式碼其餘部分的偵錯工具資訊會放在 PDB 檔案中。

### <a name="zi"></a>/ZI

**/Zi**選項與 **/zi**類似，但它會以支援 [[編輯後繼續](/visualstudio/debugger/edit-and-continue-visual-cpp)] 功能的格式產生 PDB 檔案。 若要使用 [編輯後繼續] 調試功能，您必須使用此選項。 [編輯後繼續] 功能對於開發人員的生產力很有用，但可能會導致程式碼大小、效能和編譯器一致性的問題。 因為大部分的優化與 [編輯後繼續] 不相容，所以使用 **/zi**會停用程式碼中的任何 `#pragma optimize` 語句。 **/Zi**選項也與使用[ &#95; &#95;行&#95; &#95;預先定義宏](../../preprocessor/predefined-macros.md)不相容;以 **/zi**編譯的程式碼不能使用 **&#95; &#95;line&#95;** 做為非類型樣板引數，雖然 **&#95; &#95;行&#95;** 可以在宏擴充中使用。

**/Zi**選項會強制執行在編譯中使用的[/gy （啟用函式層級連結）](gy-enable-function-level-linking.md)和[/FC （診斷中的原始程式碼檔完整路徑）](fc-full-path-of-source-code-file-in-diagnostics.md)選項。

**/Zi**與[/Clr （Common Language Runtime 編譯）](clr-common-language-runtime-compilation.md)不相容。

> [!NOTE]
> **/Zi**選項僅適用于以 x86 和 x64 處理器為目標的編譯器;以 ARM 處理器為目標的編譯器無法使用此編譯器選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 設定**屬性** > **CC++ /**  > **一般** 屬性頁。

1. 修改 [**調試資訊格式**] 屬性。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
