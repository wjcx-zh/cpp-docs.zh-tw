---
title: "-Z7，-Zi、 ZI （偵錯資訊格式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b80339192a7d335b0989ac8a67446c0f5716a76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)
選取為程式所建立的偵錯資訊類型，以及此資訊是保留在物件檔 (.obj) 還是在程式資料庫 (PDB)。  
  
## <a name="syntax"></a>語法  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>備註  
 請參閱下表描述的選項。  
  
 無  
 不產生偵錯資訊，讓編譯快一些。  
  
 **/Z7**  
 產生 .obj 檔案，其中包含供偵錯工具使用的完整符號偵錯資訊。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。 不會產生 .pdb 檔案。  
  
 沒有 .pdb 檔，對散發程式庫的協力廠商來說有好處。 不過，在連結階段和偵錯期間就必須要有先行編譯標頭檔的 .obj 檔。 如果只在.pch 物件檔中輸入資訊 （和任何程式碼） 時，您也必須使用編譯[/Yl （插入偵錯程式庫的 PCH 參考）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)。  
  
 **/Zi**  
 產生程式資料庫 (PDB)，內含與偵錯工具一起使用的類型資訊和符號偵錯資訊。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。  
  
 **/Zi**不會影響最佳化。 不過， **/Zi**意味著**偵錯**; 請參閱[/DEBUG （產生偵錯資訊）](../../build/reference/debug-generate-debug-info.md)如需詳細資訊。  
  
 類型資訊是放置於 .pdb 檔中，而不是 .obj 檔中。  
  
 您可以使用[/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)與**/Zi**，而**/Gm**不提供，以編譯時**/Z7**。  
  
 編譯時**/Zi**和**/clr**、<xref:System.Diagnostics.DebuggableAttribute>屬性將不會放在組件中繼資料; 您必須指定它在原始程式碼中，如果您要它。 這個屬性可能影響應用程式的執行階段效能。 如需有關可偵錯屬性如何影響效能，以及如何修改的效能影響的詳細資訊，請參閱[使映像更容易進行偵錯](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。  
  
 **/ZI**  
 產生其格式可支援 [編輯後繼續] 功能的程式資料庫 (如上所述)。 如果您希望使用「編輯後繼續」偵錯，就必須使用這個選項。 由於大部分最佳化都與 「 編輯後繼續 不相容，使用**/ZI**停用任何`#pragma optimize`程式碼中的陳述式。  
  
 **/ZI**導致[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路徑的原始程式碼檔中診斷）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)以用於您的編譯。  
  
 **/ZI**與不相容[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
> [!NOTE]
>  **/ZI**僅供以 x86 和 x64 處理器; 為目標的編譯器這個編譯器選項不適用於 ARM 處理器為目標的編譯器。  
  
 編譯器的程式資料庫命名*專案*.pdb。 如果您編譯沒有專案的檔案時，編譯器會建立一個名為 VC*x*0.pdb 其中*x*是主要版本的[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]使用中。 編譯器會將 PDB 的名稱嵌入每一個使用這個選項建立的 .obj 檔案，並將偵錯工具指向符號和行號資訊的位置。 使用這個選項時，您的 .obj 檔案會變得小一些，因為偵錯資訊是儲存在 .pdb 檔案中，而不是儲存在 .obj 檔案中。  
  
 如果您從使用這個選項編譯的物件建立程式庫，則關聯的 .pdb 檔案必須在程式庫連結至程式時可供使用。 因此，如果您要散發程式庫，就必須同時散發 PDB。  
  
 若要建立含有偵錯資訊，而不使用.pdb 檔案的程式庫，您必須選取編譯器的 C 7.0 相容 (**/Z7**) 選項。 如果您使用先行編譯標頭檔選項，先行編譯標頭檔與原始程式碼其餘部分的偵錯資訊都會置入 PDB 中。 **/Yd**指定程式資料庫選項時，會忽略選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**偵錯資訊格式**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)