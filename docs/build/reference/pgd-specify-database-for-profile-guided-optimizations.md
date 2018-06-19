---
title: /PGD （指定特性指引最佳化的資料庫） |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7685f99137a1b599a5f9020fac9e3cae4ba3bc3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378440"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (指定特性指引最佳化資訊庫)

**/PGD 選項已被取代。** 在 Visual Studio 2015 中，從偏好[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)連結器選項改為。 這個選項用來指定.pgd 檔用於特性指引最佳化程序的名稱。

## <a name="syntax"></a>語法

> **/PGD:**_檔名_

## <a name="argument"></a>引數

*filename*<br/>
指定用來存放執行計畫的相關資訊的.pgd 檔的名稱。

## <a name="remarks"></a>備註

使用已被取代時[/ltcg: pginstrument](../../build/reference/ltcg-link-time-code-generation.md)選項，請使用 **/PGD**指定非預設名稱或為.pgd 檔的位置。 如果您未指定 **/PGD**，.pgd 檔基準名稱等同於輸出檔 （.exe 或.dll） 基底名稱，並從中連結已叫用的相同目錄中建立。

使用已被取代時 **/ltcg: pgoptimize**選項，請使用 **/PGD**選項來指定要用來建立最佳化映像的.pgd 檔的名稱。 *Filename*引數應該符合*filename*指定至 **/ltcg: pginstrument**。

如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **最佳化**屬性頁。

1. 修改**特性指引資料庫**屬性。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
