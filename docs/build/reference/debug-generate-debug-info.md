---
title: /DEBUG (產生偵錯資訊)
ms.date: 05/16/2019
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
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837149"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (產生偵錯資訊)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>備註

**/DEBUG** 選項會建立可執行檔的偵錯資訊。

連結器會將偵錯資訊置於程式資料庫 (PDB) 檔案中。 它會在後續的程式建置期間更新 PDB。

為偵錯建立的可執行檔 (.exe 檔案或 DLL) 會包含對應 PDB 的名稱和路徑。 當您對程式偵錯時，偵錯工具會讀取內嵌名稱，並使用 PDB。 連結器會使用程式的基礎名稱和副檔名 .pdb 為程式資料庫命名，並將路徑內嵌於其建立之處。 若要覆寫此預設值，請設定 [/PDB](pdb-use-program-database.md)，並指定不同的檔案名稱。

Visual Studio 2017 及更新版本有提供 **/DEBUG:FASTLINK** 選項。 此選項會將用來建置可執行檔的私用符號資訊保存在個別編譯產品中。 它會產生在用來建置可執行檔的物件檔案和程式庫中的偵錯資訊中編製索引的有限 PDB，而不是進行完整複製。 此選項的連結速度可達到完整 PDB 產生的二到四倍，因此如果您在本機偵錯，並且有可用的組建產品，建議您使用此選項。 當必要的組建產品無法使用時 (例如，當可執行檔部署在另一部電腦上時)，這個有限的 PDB 無法用於偵錯。 在開發人員命令提示字元中，您可以使用 mspdbcmf.exe 工具從這個有限的 PDB 產生完整的 PDB。 在 Visual Studio 中，使用會產生完整 PDB 檔案的 [專案] 或 [建置] 功能表項目，來建立專案或方案的完整 PDB。

**/DEBUG:FULL** 選項會將所有私用符號資訊從個別編譯產品 (物件檔案和程式庫) 移置單一 PDB 中，而這可能是連結最耗時的部分。 不過，在沒有任何其他組建產品可用時 (例如在部署可執行檔時)，完整 PDB 可用來偵錯可執行檔。

**/DEBUG:NONE** 選項不會產生 PDB。

當您指定 **/DEBUG** 而未指定其他選項時，針對命令列和 Makefile 組建、針對 Visual Studio IDE 中的發行組建，以及針對 Visual Studio 2015 和更早版本中的偵錯和發行組建，連結器都會預設為 **/DEBUG:FULL**。 從 Visual Studio 2017 開始，當您為偵錯組建指定 **/DEBUG** 選項時，IDE 中的建置系統將會預設為 **/DEBUG:FASTLINK**。 其他預設值保持不變，以維護回溯相容性。

編譯器的 [C7 相容](z7-zi-zi-debug-information-format.md)(/Z7) 選項會使編譯器將偵錯資訊保存在 .obj 檔案中。 您也可以使用[程式資料庫](z7-zi-zi-debug-information-format.md) (/Zi) 編譯器選項，將偵錯資訊儲存在 .obj 檔案的 PDB 中。 連結器會先在撰寫於 .obj 檔案的對路徑中尋找物件的 PDB，然後再尋找包含 .obj 檔案的目錄。 您無法指定物件的 PDB 檔案名稱或連結器的位置。

當指定 /DEBUG 時，會隱含 [/INCREMENTAL](incremental-link-incrementally.md)。

/DEBUG 會將 [/OPT](opt-optimizations.md) 選項的預設值從 REF 變更為 NOREF，以及從 ICF 變更為 NOICF，因此如果您要使用原始預設值，您必須明確指定 /OPT:REF 或 /OPT:ICF。

您無法建立包含偵錯資訊的 .exe 或 .dll。 偵錯資訊一律會放在 .obj 或 .pdb 檔案中。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [偵錯] 屬性頁。

1. 修改 [產生偵錯資訊] 以產生 PDB。 這可在 Visual Studio 2017 和更新版本中依預設啟用 /DEBUG:FASTLINK。

1. 修改 [產生完整程式資料庫檔案] 屬性以啟用 /DEBUG:FULL，讓每個累加組建都能產生完整的 PDB。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
