---
title: "-Z7，-Zi、 ZI （偵錯資訊格式） |Microsoft 文件"
ms.custom: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6e3de89c5336cda98960b67b80932df8f67d183
ms.sourcegitcommit: 2cca90d965f76ebf1d741ab901693a15d5b8a4df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)

指定為您的程式，以及這項資訊保留在目的檔或在程式資料庫 (PDB) 檔案中建立的偵錯資訊類型。

## <a name="syntax"></a>語法

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>備註

下列各節描述偵錯資訊格式選項。  
  
### <a name="none"></a>無

根據預設，如果偵錯資訊格式未不指定任何選項，編譯器會產生任何偵錯資訊，讓編譯快一些。  
  
### <a name="z7"></a>/Z7

**/Z7**選項產生*物件檔案*，具有.obj 延伸，包含完整符號偵錯資訊用於偵錯工具的檔案。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。 否*PDB 檔案*，會產生.pdb 副檔名的檔案。

「 散發者 」 的協力廠商程式庫時，會有沒有 PDB 檔案的優點。 不過，先行編譯標頭的物件檔案會需要連結階段和偵錯。 如果只在.pch 物件檔中輸入資訊 （和任何程式碼） 時，您也必須使用[/Yl （插入偵錯程式庫的 PCH 參考）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)選項，預設會啟用此選項。

### <a name="zi"></a>/Zi

**/Zi**選項會產生 PDB 檔，其中包含類型資訊和符號偵錯資訊用於偵錯工具。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。

使用**/Zi**不會影響最佳化。 不過， **/Zi**意味著**偵錯**; 請參閱[/DEBUG （產生偵錯資訊）](../../build/reference/debug-generate-debug-info.md)如需詳細資訊。

當**/Zi**指定，則型別資訊會放在 PDB 檔案中，而不是在目的檔。

您可以使用[/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)搭配**/Zi**，但**/Gm**時不可以使用**/Z7**指定。

當您同時指定兩者**/Zi**和**/clr**、<xref:System.Diagnostics.DebuggableAttribute>屬性不放在組件中繼資料。 如果您想要它，您必須在原始程式碼中指定它。 這個屬性可能影響應用程式的執行階段效能。 如需有關如何**Debuggable**屬性會影響效能，以及如何您可以修改的效能影響，請參閱[使映像更容易進行偵錯](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

### <a name="zi"></a>/ZI

**/ZI**選項會產生 PDB 檔格式可支援[編輯後繼續](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 如果您希望使用「編輯後繼續」偵錯，就必須使用這個選項。 [編輯後繼續] 功能可用於開發人員生產力，但可能會導致編譯器一致性、 程式碼大小和效能問題。 由於大部分最佳化都與 「 編輯後繼續 不相容，使用**/ZI**停用任何`#pragma optimize`程式碼中的陳述式。 **/ZI**選項也是使用與不相容[&#95; &#95;資料行 &#95; #95;預先定義巨集](../../preprocessor/predefined-macros.md)。 使用程式碼編譯**/ZI**不能使用**&#95; &#95;資料行 &#95; #95;**當做非類型樣板引數，雖然**&#95; &#95;資料行 &#95; #95;**可以用巨集展開中。

**/ZI**選項會強制兩者[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路徑的原始程式碼檔中診斷）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)用於您所編譯的選項。

**/ZI**與不相容[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**選項僅供以 x86 和 x64 處理器為目標的編譯器; 這個編譯器選項不適用於 ARM 處理器為目標的編譯器。

編譯器命名 PDB 檔案*專案*.pdb。 如果您編譯專案以外的檔案時，編譯器會建立名為 VC 的 PDB 檔案*x*0.pdb，其中*x*是使用 Visual Studio 版本的主要版本號碼。 編譯器會將 PDB 的名稱嵌入每一個使用這個選項建立的 .obj 檔案，並將偵錯工具指向符號和行號資訊的位置。 當您使用此選項時，您的.obj 檔案較小，因為偵錯資訊儲存在.pdb 檔案，而不是.obj 檔中。

如果您從使用這個選項編譯的物件建立程式庫，則關聯的 .pdb 檔案必須在程式庫連結至程式時可供使用。 因此，如果您要散發程式庫，就必須同時散發 PDB。

若要建立含有偵錯資訊，而不使用.pdb 檔案的程式庫，您必須選取編譯器的 C 7.0 相容 (**/Z7**) 選項。 如果您使用先行編譯標頭選項，先行編譯標頭與原始程式碼其餘偵錯資訊置於 PDB 檔案。 **/Yd**指定程式資料庫選項時，會忽略選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 開啟**組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**偵錯資訊格式**屬性。 選擇**確定**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  

