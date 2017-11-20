---
title: "-DEBUG （產生偵錯資訊） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs: C++
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5752b6ab9f2af7c54aedc611eaae2b7f98b75ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="debug-generate-debug-info"></a>/DEBUG (產生偵錯資訊)
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>備註  

**偵錯**選項會建立可執行檔的偵錯資訊。    
  
連結器會將偵錯資訊放入程式資料庫 (PDB) 檔。 它會在程式的後續組建期間更新 PDB。  
  
建立偵錯執行檔 （.exe 檔或 DLL） 包含的名稱和路徑的相對應的 PDB。 偵錯工具會讀取內嵌的名稱，並使用 PDB，當您偵錯程式。 連結器會使用程式和副檔名.pdb 的基底名稱來命名程式資料庫，並嵌入其建立位置的路徑。 若要覆寫此預設值，設定[/PDB](../../build/reference/pdb-use-program-database.md)並指定不同的檔案名稱。  

**/Debug: fastlink**選項會將用來建置可執行檔的個別編譯產品中的私用符號資訊。 它會產生有限的 PDB 編製索引到目的檔和程式庫用來建置可執行檔，而不是進行完整複本的偵錯資訊。 此選項可以二到四次的最快速度產生完整 PDB 連結，而且當您在本機偵錯，且有可用的組建產品建議。 這個限制的 PDB 無法用於偵錯時的必要的建置項產品不可以使用，例如在另一部電腦上部署之可執行檔時。 在開發人員命令提示字元中，您可以使用 mspdbcmf.exe 工具，從這個限制的 PDB 產生完整的 PDB。 在 Visual Studio 中，用來產生完整的 PDB 檔案的專案或建置功能表項目來建立專案或方案的完整 PDB。  
  
**/Debug: full**選項將所有的私用符號資訊從個別編譯產品 （目的檔和程式庫） 移到單一的 PDB，而且可以是下列最耗時的組件的連結。 不過，完整的 PDB 可以用於任何其他建置產品時可以使用，例如可執行檔部署時，偵錯可執行檔。  
  
**偵錯： 無**選項不會產生 PDB。  
  
當您指定**偵錯**連結器預設為不搭配任何其他選項， **/debug: full**命令列和 makefile 建置，發行組建的 Visual Studio IDE 和偵錯和發行在 Visual Studio 2015 和較早版本中建置。 從 Visual Studio 2017，在 IDE 中的建置系統預設值為**/debug: fastlink**當您指定**偵錯**選項偵錯組建。 其他預設值是不變，為了維持回溯相容性。  
  
編譯器的[C7 相容](../../build/reference/z7-zi-zi-debug-information-format.md)(/ Z7) 選項可讓編譯器在.obj 檔中保留偵錯資訊。 您也可以使用[程式資料庫](../../build/reference/z7-zi-zi-debug-information-format.md)(/Zi) 編譯器選項，來偵錯資訊儲存在.obj 檔案的 PDB。 連結器會尋找物件的 PDB 第一次在.obj 檔案，以撰寫的絕對路徑，然後再搜尋含有.obj 檔案的目錄。 您無法指定物件的 PDB 檔案名稱或位置來連結器。  
  
[/ 增量](../../build/reference/incremental-link-incrementally.md)隱含指定 /DEBUG。  
  
/ DEBUG 變更預設值， [/opt](../../build/reference/opt-optimizations.md)選項從 REF NOREF 與 ICF NOICF，所以如果您想要的原始預設值，您必須明確指定 /opt: ref 或 /opt: icf。  
  
您不可能建立.exe 或.dll 包含偵錯資訊。 偵錯資訊永遠會放在.obj 或.pdb 檔案。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**偵錯**屬性頁。  
  
4.  修改**產生偵錯資訊**屬性來啟用產生 PDB。 這預設會在 Visual Studio 2017 讓 /debug: fastlink。  
  
4.  修改**產生完整的程式資料庫檔**屬性來啟用針對每次累加建置完整的 PDB 產生的 /debug: full。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
