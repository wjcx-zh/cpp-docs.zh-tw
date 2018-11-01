---
title: /DEBUG (產生偵錯資訊)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
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
ms.openlocfilehash: 579f83298fb272182cf6f1904af38c323bae2751
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625286"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (產生偵錯資訊)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>備註

**/ 偵錯**選項會建立可執行檔的偵錯資訊。

連結器會將偵錯資訊放入程式資料庫 (PDB) 檔案。 它會在後續的程式組建期間更新 PDB。

建立可執行檔 （.exe 檔或 DLL） 進行偵錯包含的名稱和路徑的相對應的 PDB。 偵錯工具會讀取內嵌的名稱，並使用 PDB，當您偵錯程式。 連結器命名程式資料庫，使用 程式和副檔名.pdb 的基底名稱，並將內嵌建立所在的路徑。 若要覆寫此預設值，請設定[/PDB](../../build/reference/pdb-use-program-database.md)並指定不同的檔案名稱。

**/Debug: fastlink**選項是可在 Visual Studio 2017 及更新版本。 這個選項會用來建置可執行檔的個別編譯產品中，將私用符號資訊。 它會產生有限的 PDB 編製索引中的物件檔案和用來建置可執行檔，而不是進行完整複製的程式庫的偵錯資訊。 這個選項可以連結兩個到完整的 PDB 產生速度快四倍，並建議當您在本機偵錯，並有可用的組建產品。 無法偵錯無法使用，例如可執行檔在另一部電腦上的部署時所需的建置產品時要使用此有限的 PDB。 在開發人員命令提示字元中，您可以使用 mspdbcmf.exe 工具，從這個有限的 PDB 產生完整的 PDB。 在 Visual Studio 中使用的專案 或 建置 功能表項目來產生完整的 PDB 檔案建立專案或方案的完整 PDB。

**/Debug: full**選項將從個別編譯產品 （目的檔和程式庫） 的所有私用符號資訊移到單一的 PDB，，而且可以是最耗時的組件的連結。 不過，完整的 PDB 可以用於任何其他組建產品時使用，例如可執行檔部署時，偵錯可執行檔。

**/ 偵錯： 無**選項不會產生 PDB。

當您指定 **/ 偵錯**無其他選項，連結器將預設為 **/debug: full**命令列 和 makefile 組建版本組建的 Visual Studio IDE 中，以及偵錯和發行Visual Studio 2015 和更早版本中建置。 從 Visual Studio 2017 中，在 IDE 中的建置系統預設值為 **/debug: fastlink**當您指定 **/ 偵錯**選項表示偵錯組建。 其他預設值是不變，為了維持回溯相容性。

編譯器[C7 相容](../../build/reference/z7-zi-zi-debug-information-format.md)(/ Z7) 選項可讓編譯器保留.obj 檔中的偵錯資訊。 您也可以使用[程式資料庫](../../build/reference/z7-zi-zi-debug-information-format.md)(/Zi) 編譯器選項，以將偵錯的資訊儲存在.obj 檔案的 PDB。 連結器物件的 PDB 會先尋找在.obj 檔案中，撰寫的絕對路徑，然後再搜尋含有.obj 檔案的目錄。 您無法指定物件的 PDB 檔案名稱或連結器的位置。

[/ 增量](../../build/reference/incremental-link-incrementally.md)就會隱含指定 /DEBUG 時。

/ 偵錯變更的預設值[/opt](../../build/reference/opt-optimizations.md)選項從 REF NOREF 進出 ICF NOICF，所以如果您想要的原始預設值，您必須明確指定 /opt: ref 或 /opt: icf。

您不可能建立.exe 或.dll，其中包含偵錯資訊。 偵錯資訊一律放在.obj 或.pdb 檔。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**產生偵錯資訊**啟用 PDB 產生的屬性。 如此 /debug: fastlink 預設會在 Visual Studio 2017。

1. 修改**產生完整的程式資料庫檔**屬性，針對每次累加建置完整的 PDB 產生讓 /debug: full。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
