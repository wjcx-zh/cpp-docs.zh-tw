---
title: /GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: e703c94d4a8b7cf7c70e68071959b775987f1710
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496443"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)

指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 **/GENPROFILE**並 **/FASTGENPROFILE**使用不同的預設參數。 使用 **/GENPROFILE**讓精確度優先於速度和記憶體使用量，程式碼剖析期間。 使用 **/FASTGENPROFILE**讓較小的記憶體使用量和速度優先於精確度。

## <a name="syntax"></a>語法

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**精確**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路徑**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**精確**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路徑**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]

### <a name="arguments"></a>引數

任何下列的引數來指定 **/GENPROFILE**或是 **/FASTGENPROFILE**。 此處所列的引數以管道分隔 (**|**) 是互斥的字元。 使用逗號 (**，**) 字元來分隔選項。

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
使用**COUNTER32**若要指定使用 32 位元的探查計數器，以及**COUNTER64**指定 64 位元的探查計數器。 當您指定 **/GENPROFILE**，預設值是**COUNTER64**。 當您指定 **/FASTGENPROFILE**，預設值是**COUNTER32**。

**確切** &AMP;#124; **NOEXACT**<br/>
使用**精確**指定探查的安全執行緒連鎖的遞增。 **NOEXACT**指定探查的受保護的遞增作業。 預設值是**NOEXACT**。

**MEMMAX**=*值*， **MEMMIN**=*值*<br/>
使用**MEMMAX**並**MEMMIN**在記憶體中指定定型資料的最大和最小的保留大小。 值是以位元組為單位的要保留記憶體數量。 這些值預設由內部的啟發學習法決定。

**路徑**&AMP;#124; **NOPATH**  <br/>
使用**路徑**來指定一組個別的函式的每個唯一路徑的 PGO 計數器。 使用**NOPATH**指定只有一組計數器每個函式。 當您指定 **/GENPROFILE**，預設值是**路徑**。 當您指定 **/FASTGENPROFILE**，預設值是**NOPATH** 。

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
指定在訓練期間擲回例外狀況時，是否使用額外的計數器來保持精確的計數。 使用**TRACKEH**來指定額外的計數器，確切的計數。 使用  **NOTRACKEH**指定單一計數器不會使用例外狀況的程式碼處理或不會碰到訓練情節中的例外狀況。  當您指定 **/GENPROFILE**，預設值是**TRACKEH** 。 當您指定 **/FASTGENPROFILE**，預設值是**NOTRACKEH** 。

**PGD**=*檔名*<br/>
指定 .pgd 檔的主檔名。 連結器預設使用副檔名為 .pgd 的可執行影像主檔名。

## <a name="remarks"></a>備註

**/GENPROFILE**並 **/FASTGENPROFILE**選項會告訴連結器產生支援特性指引最佳化 (PGO) 的應用程式訓練所需的程式碼剖析檢測檔案。 這些選項是在 Visual Studio 2015 新功能。 偏好使用這些選項已被取代 **/ltcg: pginstrument**， **/PGD**並 **/POGOSAFEMODE**選項和**PogoSafeMode**， **VCPROFILE_ALLOC_SCALE**並**VCPROFILE_PATH**環境變數。 應用程式訓練所產生的程式碼剖析資訊用做輸入，在建置期間執行整個程式的最佳化。 您可以設定其他選項，在應用程式訓練和建置期間控制各種效能的程式碼剖析功能。 指定的預設選項 **/GENPROFILE**提供最精確的結果，特別是針對大型且複雜的多執行緒應用程式。 **/FASTGENPROFILE**選項使用不同的預設值的較低的記憶體耗用量和更快的效能，在訓練期間，但會犧牲精確度。

當您使用建置後，執行已檢測的應用程式程式碼剖析資訊擷取 **/GENPROFILE**的 **/FASTGENPROFILE**。 當您指定時，會擷取此資訊[/USEPROFILE](useprofile.md)連結器選項，來執行分析步驟，並接著可用來引導最佳化的建置步驟。 有關如何訓練您的應用程式的詳細資訊及收集的資料的詳細資訊，請參閱[特性指引最佳化](profile-guided-optimizations.md)。

您也必須指定 **/LTCG**當您指定 **/GENPROFILE**或是 **/FASTGENPROFILE**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入 **/GENPROFILE**或是 **/FASTGENPROFILE**選項和引數**其他選項** 方塊中。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[/LTCG (連結時間產生程式碼)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
