---
title: /LINKREPROTARGET （連結重現檔案名）
description: 連結器或程式庫工具選項，用於設定連結重現的目的檔案名。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: d629c4c2665239d03f38569677fa579b6c8d37e0
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712690"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET （連結重現檔案名）

通知連結器或程式庫工具，只有在目標具有指定的檔案名時，才會產生連結重現。

## <a name="syntax"></a>語法

> **/LINKREPROTARGET：** _檔案名_

### <a name="arguments"></a>引數

**/LINKREPROTARGET：** _檔案名_\
要做為篩選依據的目的檔案名。 只有當命名的檔案是輸出目標時，才會產生連結重現。 包含空格的檔案名必須括在雙引號中。 檔案名應該包含基底名稱和副檔名，而不是路徑。

## <a name="remarks"></a>備註

**/LINKREPROTARGET**選項是用來指定要產生*連結重現*的目的檔案名。 「連結重現」是一組組建成品，可讓 Microsoft 重現連結時或程式庫作業期間發生的問題。 當您指定[/LINKREPRO](linkrepro.md)選項時，或當您在命令列組建環境中設定 @no__t 1 環境變數時，連結器或程式庫工具會產生連結重現。

在用來叫用連結器或程式庫工具的複雜組建中， **/LINKREPROTARGET**選項會很有用。 它可讓您指定連結重現的特定目標，例如*問題 .dll*。 它可讓您只有在工具產生特定檔案時，才會產生連結重現。

如需如何和何時建立連結重現的詳細資訊，請參閱 how [to report a 問題 with The Microsoft C++工具](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)組中的 < [link 重現](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)一節。

必須設定 **/LINKREPRO**和[/Out](out-output-file-name.md)選項， **/LINKREPROTARGET**選項才會有任何效果。

從 Visual Studio 2019 16.1 版開始提供 **/LINKREPROTARGET** 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 設定**屬性**  > **連結器** > **命令列** 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/LINKREPROTARGET：** _file-name_選項。 選擇 [確定] 以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)\
[/LINKREPRO](linkrepro.md)
