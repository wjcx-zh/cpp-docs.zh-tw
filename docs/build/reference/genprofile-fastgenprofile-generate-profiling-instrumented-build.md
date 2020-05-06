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
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825780"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)

指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 **/GENPROFILE**和 **/FASTGENPROFILE**使用不同的預設參數。 在分析期間，使用 **/GENPROFILE**來偏好速度和記憶體使用量的精確度。 使用 **/FASTGENPROFILE**來偏好較小的記憶體使用量，並加快精確度的速度。

## <a name="syntax"></a>語法

> **/GENPROFILE**[**：**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_|[**PATH**|**NOPATH** ] |[**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}] \
> **/FASTGENPROFILE**[**：**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_|[**PATH**|**NOPATH** ] |[**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]

### <a name="arguments"></a>引數

下列任何一個引數可以指定為 **/GENPROFILE**或 **/FASTGENPROFILE**。 此處所列的引數會以**|** 分隔號（）字元隔開，而互斥。 使用逗號（**，**）字元來分隔選項。

**COUNTER32** &#124; **COUNTER64**<br/>
使用**COUNTER32**來指定使用32位的探查計數器，並使用**COUNTER64**來指定64位的探查計數器。 當您指定 **/GENPROFILE**時，預設值為**COUNTER64**。 當您指定 **/FASTGENPROFILE**時，預設值為**COUNTER32**。

**精確**&#124; **NOEXACT**<br/>
使用**EXACT**來指定探查的安全線程連鎖增量。 **NOEXACT**會指定探查的未受保護增量作業。 預設值為**NOEXACT**。

**MEMMAX**=*值*， **MEMMIN**=*值*<br/>
使用**MEMMAX**和**MEMMIN**來指定記憶體中定型資料的最大和最小保留大小。 值是以位元組為單位的要保留記憶體數量。 這些值預設由內部的啟發學習法決定。

**路徑**&#124; **NOPATH** <br/>
使用**PATH**為函式的每個唯一路徑指定一組個別的 PGO 計數器。 使用**NOPATH**為每個函式只指定一組計數器。 當您指定 **/GENPROFILE**時，預設值是**PATH** 。 當您指定 **/FASTGENPROFILE**時，預設值為**NOPATH** 。

**TRACKEH** &#124; **NOTRACKEH** <br/>
指定在訓練期間擲回例外狀況時，是否使用額外的計數器來保持精確的計數。 使用**TRACKEH**來指定確切計數的額外計數器。 使用**NOTRACKEH**為不使用例外狀況處理的程式碼，或不會在定型案例中遇到例外狀況的腳本，指定單一計數器。  當您指定 **/GENPROFILE**時，預設值為**TRACKEH** 。 當您指定 **/FASTGENPROFILE**時，預設值為**NOTRACKEH** 。

**PGD**=*檔案名*<br/>
指定 .pgd 檔的主檔名。 連結器預設使用副檔名為 .pgd 的可執行影像主檔名。

## <a name="remarks"></a>備註

**/GENPROFILE**和 **/FASTGENPROFILE**選項會告訴連結器產生支援特性指引優化（PGO）之應用程式訓練所需的分析檢測檔案。 這些選項是 Visual Studio 2015 中的新功能。 偏好使用這些選項至已被取代的 **/ltcg： PGINSTRUMENT**、 **/PGD**和 **/POGOSAFEMODE**選項，以及**POGOSAFEMODE**、 **VCPROFILE_ALLOC_SCALE**和**VCPROFILE_PATH**環境變數。 應用程式訓練所產生的程式碼剖析資訊用做輸入，在建置期間執行整個程式的最佳化。 您可以設定其他選項，在應用程式訓練和建置期間控制各種效能的程式碼剖析功能。 **/GENPROFILE**所指定的預設選項會提供最精確的結果，特別是針對大型、複雜的多執行緒應用程式。 在定型期間， **/FASTGENPROFILE**選項會使用不同的預設值來取得較低的記憶體使用量和更快的效能，代價是準確度。

當您使用 **/FASTGENPROFILE**的 **/GENPROFILE**建立之後，當您執行已檢測的應用程式時，就會捕捉分析資訊。 當您指定[/USEPROFILE](useprofile.md)連結器選項來執行程式碼剖析步驟，然後用來引導優化的組建步驟時，就會捕捉這項資訊。 如需如何訓練應用程式的詳細資訊，以及所收集資料的詳細資訊，請參閱特性[指引優化](../profile-guided-optimizations.md)。

當您指定 **/GENPROFILE**或 **/FASTGENPROFILE**時，也必須指定 **/ltcg** 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [**連結器** > **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/GENPROFILE**或 **/FASTGENPROFILE**選項和引數。 選取 [確定]**** 儲存您的變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/LTCG (連結時間產生程式碼)](ltcg-link-time-code-generation.md)<br/>
