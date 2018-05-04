---
title: /GENPROFILE、 /FASTGENPROFILE （產生程式碼剖析檢測的建置） |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05d7961ff46661b8f6df2768591932699c3965d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)

指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 **/GENPROFILE**和 **/FASTGENPROFILE**使用不同的預設參數。 使用 **/GENPROFILE**分析期間，讓精確度優先於速度和記憶體使用量。 使用 **/FASTGENPROFILE**讓較小的記憶體使用量和速度優先於精確度。

## <a name="syntax"></a>語法

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**精確**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路徑**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**精確**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路徑**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]

### <a name="arguments"></a>引數

下列引數來指定 **/GENPROFILE**或 **/FASTGENPROFILE**。 此處所列的引數以垂直線分隔 (**|**) 字元是互斥。 使用逗號 (**，**) 字元來分隔選項。

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
使用**COUNTER32**指定的 32 位元的探查計數器用途和**COUNTER64**指定 64 位元的探查計數器。 當您指定 **/GENPROFILE**，預設值是**COUNTER64**。 當您指定 **/FASTGENPROFILE**，預設值是**COUNTER32**。

**確切** &AMP;#124; **NOEXACT**<br/>
使用**精確**指定探查的安全執行緒連鎖的遞增。 **NOEXACT**指定探查受保護的遞增作業。 預設值是**NOEXACT**。

**MEMMAX**=*值*， **MEMMIN**=*值*<br/>
使用**MEMMAX**和**MEMMIN**指定記憶體中訓練資料的最大和最小保留大小。 值是以位元組為單位的要保留記憶體數量。 這些值預設由內部的啟發學習法決定。

**路徑**&AMP;#124; **NOPATH**  <br/>
使用**路徑**來指定一組個別的每個唯一路徑的函式的 PGO 計數器。 使用**NOPATH**來只指定一組的每個函式的計數器。 當您指定 **/GENPROFILE**，預設值是**路徑**。 當您指定 **/FASTGENPROFILE**，預設值是**NOPATH** 。

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
指定在訓練期間擲回例外狀況時，是否使用額外的計數器來保持精確的計數。 使用**TRACKEH**指定確切的計數額外的計數器。 使用**NOTRACKEH**指定不使用例外狀況的程式碼的單一計數器處理或是不會碰到訓練情節的例外狀況。  當您指定 **/GENPROFILE**，預設值是**TRACKEH** 。 當您指定 **/FASTGENPROFILE**，預設值是**NOTRACKEH** 。

**PGD**=*檔名*<br/>
指定 .pgd 檔的主檔名。 連結器預設使用副檔名為 .pgd 的可執行影像主檔名。

## <a name="remarks"></a>備註

**/GENPROFILE**和 **/FASTGENPROFILE**選項會告訴連結器產生程式碼剖析檢測檔案，以支援用於特性指引最佳化 (PGO) 應用程式訓練所需。 這些選項是在 Visual Studio 2015 的新功能。 這些選項已被取代的偏好 **/ltcg: pginstrument**， **/PGD**和 **/POGOSAFEMODE**選項和**PogoSafeMode**， **VCPROFILE_ALLOC_SCALE**和**VCPROFILE_PATH**環境變數。 應用程式訓練所產生的程式碼剖析資訊用做輸入，在建置期間執行整個程式的最佳化。 您可以設定其他選項，在應用程式訓練和建置期間控制各種效能的程式碼剖析功能。 所指定的預設選項 **/GENPROFILE**提供最精確的結果，特別是針對大型、 複雜的多執行緒應用程式。 **/FASTGENPROFILE**選項會使用不同的預設值低的記憶體耗用量和更快的效能在訓練期間，但會犧牲精確度。

當您使用建置後，執行已檢測的應用程式程式碼剖析資訊擷取 **/GENPROFILE**的 **/FASTGENPROFILE**。 當您指定時，會擷取此資訊[/USEPROFILE](useprofile.md)逐步執行程式碼剖析的連結器選項，而且會用來引導最佳化的建置步驟。 如需收集的資料的詳細資訊和如何訓練您的應用程式的詳細資訊，請參閱[特性指引最佳化](profile-guided-optimizations.md)。

您也必須指定 **/LTCG**當您指定 **/GENPROFILE**或 **/FASTGENPROFILE**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入 **/GENPROFILE**或 **/FASTGENPROFILE**選項和引數到**其他選項**方塊。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[/LTCG (連結時間產生程式碼)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
