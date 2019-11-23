---
title: /LINKREPRO (連結存放庫目錄名稱)
description: 連結器或程式庫工具選項，用來設定連結重現的目錄。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686849"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (連結存放庫目錄名稱)

指示連結器或程式庫工具在指定的目錄中產生連結重現。

## <a name="syntax"></a>語法

> **/LINKREPRO：** _目錄-名稱_

### <a name="arguments"></a>引數

**/LINKREPRO：** _目錄-名稱_\
要在其中儲存連結重現的使用者指定目錄。 包含空格的目錄名稱必須括在雙引號中。

## <a name="remarks"></a>備註

**/LINKREPRO**選項是用來建立*連結重現*。 這是一組組建成品，可讓 Microsoft 重現在連結時間或程式庫作業期間發生的問題。 這適用于與連結時間程式碼產生（LTCG）、LNK1000 連結器錯誤或連結器損毀有關的問題，例如後端損毀。 當您指定 **/LINKREPRO**連結器選項時，或當您在命令列組建環境中設定 `link_repro` 環境變數時，此工具會產生連結重現。 如需詳細資訊，請參閱[如何向 Microsoft C++工具](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)組回報問題的[連結重現](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)一節。

**/LINKREPRO**連結器選項和 `link_repro` 環境變數都必須指定連結重現的輸出目錄。 在命令列或 IDE 中，使用 **/LINKREPRO：** _directory-name_選項來指定目錄。 您指定的_目錄名稱_可能是絕對或相對路徑，但目錄必須存在。 命令列選項會覆寫在 `link_repro` 環境變數中設定的任何目錄值。

如需如何將連結重現產生限制為特定目的檔案名的詳細資訊，請參閱[/LINKREPROTARGET](linkreprotarget.md)選項。 這個選項可以用來指定要產生連結重現的特定目標。 這在多次叫用連結器或程式庫工具的複雜組建中很有用。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] > **連結器** > [**命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/LINKREPRO：** _directory-name_選項。 您指定的_目錄名稱_值必須存在。 選擇 [確定] 以套用變更。

一旦產生連結重現，請再次開啟此屬性頁，以從您的組建中移除 **/LINKREPRO**選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
