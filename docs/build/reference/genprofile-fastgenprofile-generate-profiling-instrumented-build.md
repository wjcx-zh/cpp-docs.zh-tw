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
ms.openlocfilehash: a0d1678cd400801f4cb809ec3e93d333fbc6416a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041194"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)

指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。 **/GENPROFILE** 和 **/FASTGENPROFILE** 使用不同的預設參數。 在程式碼剖析期間，使用 **/GENPROFILE** 來優先使用速度和記憶體使用量的精確度。 使用 **/FASTGENPROFILE** 來優先使用較小的記憶體使用量，並加快精確度。

## <a name="syntax"></a>語法

> **/GENPROFILE** \[**：**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **EXACT** \| **NOEXACT**] \| **MEMMAX =** _#_ \| **MEMMIN =** _#_ \| \[ **PATH** \| **NOPATH**] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}] \
> **/FASTGENPROFILE** \[**：**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **EXACT** \| **NOEXACT**] \| **MEMMAX =** _#_ \| **MEMMIN =** _#_ \| [**PATH** \| **NOPATH** ] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}]

### <a name="arguments"></a>引數

您可以將下列任何引數指定為 **/GENPROFILE** 或 **/FASTGENPROFILE**。 此處所列的引數會以管道分隔 (**|**) 字元是互斥的。 使用逗號 (**、**) 字元來分隔選項。

**COUNTER32** &#124; **COUNTER64**<br/>
使用 **COUNTER32** 來指定使用32位探查計數器，並使用 **COUNTER64** 來指定64位探查計數器。 當您指定 **/GENPROFILE**時，預設值為 **COUNTER64**。 當您指定 **/FASTGENPROFILE**時，預設值為 **COUNTER32**。

**確切** 的 &#124; **NOEXACT**<br/>
使用 **EXACT** 來指定探查的安全線程連鎖增量。 **NOEXACT** 指定探查的未受保護增量作業。 預設值為 **NOEXACT**。

**MEMMAX** =*value*、 **MEMMIN** = *值*<br/>
使用 **MEMMAX** 和 **MEMMIN** 來指定在記憶體中定型資料的最大和最小保留大小。 值是以位元組為單位的要保留記憶體數量。 這些值預設由內部的啟發學習法決定。

**路徑**  &#124; **NOPATH** <br/>
使用 **PATH**  為函式的每個唯一路徑指定一組個別的 PGO 計數器。 使用 **NOPATH**  只針對每個函式指定一組計數器。 當您指定 **/GENPROFILE**時，預設值為 **PATH** 。 當您指定 **/FASTGENPROFILE**時，預設值為 **NOPATH** 。

**TRACKEH**  &#124; **NOTRACKEH** <br/>
指定在訓練期間擲回例外狀況時，是否使用額外的計數器來保持精確的計數。 使用 **TRACKEH**  來指定確切計數的額外計數器。 使用 **NOTRACKEH**  可針對未使用例外狀況處理的程式碼，或在定型案例中未遇到例外狀況的程式碼，指定單一計數器。  當您指定 **/GENPROFILE**時，預設值為 **TRACKEH** 。 當您指定 **/FASTGENPROFILE**時，預設值為 **NOTRACKEH** 。

**PGD** =*檔案名*<br/>
指定 .pgd 檔的主檔名。 連結器預設使用副檔名為 .pgd 的可執行影像主檔名。

## <a name="remarks"></a>備註

**/GENPROFILE**和 **/FASTGENPROFILE**選項會指示連結器產生程式碼剖析檢測檔案，以支援特性指引優化 (PGO) 的應用程式定型。 這些選項是 Visual Studio 2015 中的新選項。 偏好將這些選項設為已被取代的 **/ltcg： PGINSTRUMENT**、 **/PGD** 和 **/POGOSAFEMODE** 選項以及 **POGOSAFEMODE**、 **VCPROFILE_ALLOC_SCALE** 和 **VCPROFILE_PATH** 的環境變數。 應用程式訓練所產生的程式碼剖析資訊用做輸入，在建置期間執行整個程式的最佳化。 您可以設定其他選項，在應用程式訓練和建置期間控制各種效能的程式碼剖析功能。 **/GENPROFILE**指定的預設選項提供最精確的結果，尤其是大型、複雜的多執行緒應用程式。 在定型期間， **/FASTGENPROFILE** 選項會使用不同的預設值來取得較低的記憶體使用量和更快速的效能，以節省精確度。

當您在使用 **/FASTGENPROFILE**的 **/GENPROFILE**建立之後，執行已檢測的應用程式時，就會捕獲分析資訊。 當您指定 [/USEPROFILE](useprofile.md) 連結器選項來執行程式碼剖析步驟，然後用來引導優化的組建步驟時，就會捕捉這項資訊。 如需有關如何定型應用程式的詳細資訊，以及有關所收集資料的詳細資訊，請參閱特性 [指引優化](../profile-guided-optimizations.md)。

當您指定 **/GENPROFILE**或 **/FASTGENPROFILE**時，也必須指定 **/ltcg** 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/GENPROFILE**或 **/FASTGENPROFILE**選項和引數。 選取 [確定]**** 儲存您的變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/LTCG (連結時產生程式碼) ](ltcg-link-time-code-generation.md)<br/>
