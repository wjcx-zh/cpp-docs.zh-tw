---
title: /USEPROFILE （使用 LTCG 使用 PGO 資料）
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 4b780bed3b92b874f2bf18fb0235e8e2baf95ae9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550627"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (執行緒安全模式中的執行 PGO)

這個連結器選項，並搭配[/LTCG (連結時間程式碼產生](ltcg-link-time-code-generation.md)會告訴連結器使用特性指引最佳化 (PGO) 定型資料來建置。

## <a name="syntax"></a>語法

> **/USEPROFILE**[**:**{**激進**|**PGD =**_filename_}]

### <a name="arguments"></a>引數

**積極**<br/>
這個選擇性的引數會指定在最佳化程式碼產生期間，應該使用積極的速度最佳化。

**PGD**=*檔名*<br/>
指定 .pgd 檔的主檔名。 根據預設，連結器會使用副檔名為.pgd 的基底的可執行檔名稱。

## <a name="remarks"></a>備註

**/USEPROFILE**連結器選項可搭配使用 **/LTCG**產生或更新最佳化的組建 PGO 訓練資料為基礎。 它相當於已被取代**除了**並 **/ltcg: pgoptimize**選項。

選擇性**激進**引數會停用大小相關啟發學習法來嘗試速度最佳化。 這可能會導致大幅增加您的可執行檔的大小，且可能不會增加結果的速度最佳化。 您應該設定檔，並比較使用和未使用的結果**激進**。 必須指定這個引數明確;它不是預設啟用。

**PGD**引數會指定使用中的相同訓練資料.pgd 檔的選擇性名稱[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。 它相當於已被取代 **/PGD**切換。 根據預設，或者如果沒有任何*filename*指定，則具有相同的基底名稱，因為會使用可執行檔的.pgd 檔。

**/USEPROFILE**連結器選項的新 Visual Studio 2015。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **最佳化**屬性頁。

1. 在 [**連結時產生程式碼**] 屬性中，選擇**使用連結時間產生程式碼 (/ LTCG)**。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 請輸入 **/USEPROFILE**選項，並選擇性引數**其他選項** 方塊中。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)<br/>
[特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
