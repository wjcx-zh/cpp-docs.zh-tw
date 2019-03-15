---
title: /PGD (指定特性指引最佳化資訊庫)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812196"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (指定特性指引最佳化資訊庫)

**/PGD 選項已被取代。** 在 Visual Studio 2015 中，從偏好[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)連結器改為選項。 此選項用來指定.pgd 檔用於特性指引最佳化程序的名稱。

## <a name="syntax"></a>語法

> **/PGD:**_檔名_

## <a name="argument"></a>引數

*filename*<br/>
指定用來保存執行計劃的相關資訊的.pgd 檔案名稱。

## <a name="remarks"></a>備註

使用已被取代時[/ltcg: pginstrument](ltcg-link-time-code-generation.md)選項，請使用 **/PGD**指定非預設名稱或為.pgd 檔的位置。 如果您未指定 **/PGD**，.pgd 檔基準名稱等同於輸出檔 （.exe 或.dll） 基底名稱，並建立的連結已叫用的相同目錄中。

使用已被取代時 **/ltcg: pgoptimize**選項，請使用 **/PGD**選項來指定要用來建立最佳化映像的.pgd 檔案名稱。 *檔名*引數應該符合*filename*指定給 **/ltcg: pginstrument**。

如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../profile-guided-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **最佳化**屬性頁。

1. 修改**特性指引資料庫**屬性。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
