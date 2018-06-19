---
title: /USEPROFILE （使用 PGO 資料與 LTCG） |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156a571eaa3db31b8c5345f1550346503651665d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377989"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (執行緒安全模式中的執行 PGO)

這個連結器選項，連同[/LTCG (連結時間程式碼產生](ltcg-link-time-code-generation.md)會告訴連結器，以建置使用特性指引最佳化 (PGO) 的定型資料。

## <a name="syntax"></a>語法

> **/USEPROFILE**[**:**{**主動**|**PGD =**_filename_}]

### <a name="arguments"></a>引數

**積極**<br/>
此選擇性引數會指定應透過最佳化程式碼產生期間積極速度最佳化。

**PGD**=*檔名*<br/>
指定 .pgd 檔的主檔名。 根據預設，連結器會使用副檔名為.pgd 的可執行檔的基底檔案名稱。

## <a name="remarks"></a>備註

**/USEPROFILE**連結器選項會搭配 **/LTCG**產生或更新最佳化的組建根據 PGO 訓練資料。 它相當於已被取代**除了**和 **/ltcg: pgoptimize**選項。

選擇性**主動**引數會停用嘗試速度最佳化大小相關啟發學習法的大小。 這可能會導致大幅增加您的可執行檔的大小及可能不會增加結果的速度最佳化。 您應該設定檔，並比較使用和未使用的結果**主動**。 這個引數必須指定明確;它不會預設啟用。

**PGD**引數會指定使用中的相同訓練資料.pgd 檔的選擇性名稱[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。 它相當於已被取代 **/PGD**切換。 根據預設，或者如果沒有任何*filename*指定，則具有相同的基底名稱，可執行檔所使用的.pgd 檔。

**/USEPROFILE**連結器選項的新功能 Visual Studio 2015。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **最佳化**屬性頁。

1. 在**連結時間產生程式碼**屬性中，選擇**使用連結時間程式碼產生 (/ LTCG)**。

1. 選取**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入 **/USEPROFILE**選項和選擇性引數到**其他選項**方塊。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)<br/>
[特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
