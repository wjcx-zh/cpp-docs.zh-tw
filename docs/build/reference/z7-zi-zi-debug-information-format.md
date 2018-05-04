---
title: -Z7，-Zi、 ZI （偵錯資訊格式） |Microsoft 文件
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86605b8fd47c0febedfc9ab022dfc2c2728822a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)

指定為您的程式，以及這項資訊保留在目的檔或在程式資料庫 (PDB) 檔案中建立的偵錯資訊類型。

## <a name="syntax"></a>語法

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>備註

程式碼進行編譯和建置偵錯模式中時，編譯器會產生函式和變數、 型別資訊，以及以供偵錯工具的線條數字位置的符號名稱。 這個符號的偵錯資訊可以包含在編譯器產生的物件檔 （.obj 檔），或在不同的 PDB 檔案 （.pdb 檔案） 的可執行檔。  下列各節描述偵錯資訊格式選項。  
  
### <a name="none"></a>無

根據預設，如果偵錯資訊格式未不指定任何選項，編譯器會產生任何偵錯資訊，讓編譯快一些。  
  
### <a name="z7"></a>/Z7

**/Z7**選項會產生也包含完整符號偵錯資訊使用與偵錯工具的目的檔。 這些物件的檔案和已建置的可執行檔可以大幅增加比沒有偵錯資訊的檔案。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。 會不產生任何 PDB 檔案。

「 散發者 」 的協力廠商程式庫的偵錯版本，會有沒有 PDB 檔案的優點。 不過，任何先行編譯標頭的物件檔案會需要在程式庫連結階段，並進行偵錯。 如果只.pch 物件檔中所輸入的資訊 （和任何程式碼） 時，您也必須使用[/Yl （插入偵錯程式庫的 PCH 參考）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)選項，當您建置程式庫時，根據預設，已啟用。

[/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)選項時，不使用 **/Z7**指定。

### <a name="zi"></a>/ZI

**/Zi**選項會產生個別的 PDB 檔案，其中包含所有符號偵錯資訊用於偵錯工具。 偵錯資訊不會包含在目的檔或可執行檔，讓它們更小。

使用 **/Zi**不會影響最佳化。 不過， **/Zi**意味著**偵錯**; 請參閱[/DEBUG （產生偵錯資訊）](../../build/reference/debug-generate-debug-info.md)如需詳細資訊。


當您同時指定兩者 **/Zi**和 **/clr**、<xref:System.Diagnostics.DebuggableAttribute>屬性不放在組件中繼資料。 如果您想要它，您必須在原始程式碼中指定它。 這個屬性可能影響應用程式的執行階段效能。 如需有關如何**Debuggable**屬性會影響效能，以及如何您可以修改的效能影響，請參閱[使映像更容易進行偵錯](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

編譯器命名 PDB 檔案*專案*.pdb。 如果您編譯專案以外的檔案時，編譯器會建立名為 VC 的 PDB 檔案*x*.pdb，其中*x*串連中使用的編譯器版本的主要和次要版本號碼。 編譯器會使用這個選項，偵錯工具指向符號和行號資訊的位置建立每個目的檔中內嵌 PDB 和識別的加上簽章的名稱。 名稱和 PDB 檔案中的簽章必須符合偵錯工具中載入符號的可執行檔。 WinDBG 偵錯工具可以載入使用的不相符的符號`.symopt+0x40`命令。 Visual Studio 沒有類似的選項，來載入符號不相符。

如果您從使用編譯的物件建立文件庫 **/Zi**，程式庫連結至程式時，關聯的.pdb 檔案必須能夠使用。 因此，如果您要散發程式庫，您也必須散發 PDB 檔案。 若要建立不使用 PDB 檔案包含偵錯資訊的程式庫，您必須選取 **/Z7**選項。 如果您使用先行編譯標頭選項，先行編譯標頭與原始程式碼其餘偵錯資訊置於 PDB 檔案。

### <a name="zi"></a>/ZI

**/ZI**選項是類似於 **/Zi**，但它會產生 PDB 檔格式可支援[編輯後繼續](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 若要使用 編輯後繼續 」 偵錯功能，您必須使用此選項。 [編輯後繼續] 功能可用於開發人員生產力，但可能會導致程式碼大小、 效能及編譯器一致性問題。 由於大部分最佳化都與 「 編輯後繼續 不相容，使用 **/ZI**停用任何`#pragma optimize`程式碼中的陳述式。 **/ZI**選項也是使用與不相容[ &#95;&#95;列&#95;&#95;預先定義巨集](../../preprocessor/predefined-macros.md); 程式碼使用編譯 **/ZI**不能使用 **&#95;&#95;列&#95;&#95;** 當做非類型樣板引數，雖然 **&#95;&#95;列&#95;&#95;** 可用巨集展開中。

**/ZI**選項會強制兩者[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路徑的原始程式碼檔中診斷）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)用於您所編譯的選項。

**/ZI**與不相容[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**選項僅供以 x86 和 x64 處理器為目標的編譯器; 這個編譯器選項不適用於 ARM 處理器為目標的編譯器。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 開啟**組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**偵錯資訊格式**屬性。 選擇**確定**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  

