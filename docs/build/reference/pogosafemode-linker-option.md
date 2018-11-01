---
title: / POGOSAFEMODE (執行緒安全模式中的執行 PGO)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: f210884d693ef0d778943580b9c5a7b2ec2ea336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544426"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (執行緒安全模式中的執行 PGO)

**/POGOSAFEMODE 選項已被取代，從 Visual Studio 2015 開始**。 使用[/GENPROFILE： 確切](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)並 **/GENPROFILE:NOEXACT**改為選項。 **/POGOSAFEMODE**連結器選項可讓您指定要用於設定檔資料擷取特性指引最佳化 (PGO) 期間定型執行中的安全執行緒模式建立已檢測的組建。

## <a name="syntax"></a>語法

> **/POGOSAFEMODE**

## <a name="remarks"></a>備註

特性指引最佳化 (PGO) 的程式碼剖析工作階段有兩個可能的模式：*快速模式*並*安全模式*。 當程式碼剖析處於快速模式時，它會使用遞增指令增加資料計數器。 遞增指令會較快，但不是安全執行緒。 當程式碼剖析處於安全模式時，它會使用連鎖遞增指令增加資料計數器。 這個指令會具有相同的功能，做為遞增，而且是安全執行緒，但是它是速度較慢。

**/POGOSAFEMODE**選項會設定為使用安全模式檢測的組建。 此選項只可使用時已被取代[/ltcg: pginstrument](ltcg-link-time-code-generation.md)指定，PGO 檢測連結器階段。

根據預設，PGO 程式碼剖析以快速模式運作。 **/ POGOSAFEMODE**是如果您想要使用安全模式下，才需要。

若要執行 PGO 程式碼剖析在安全模式中，您必須使用 **/GENPROFILE： 確切**（偏好選項），或使用環境變數[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md)或 連結器參數 **/POGOSAFEMODE**，這取決於系統。 如果您正在執行分析使用 x64 電腦，您必須使用連結器參數。 如果您正在執行 x86 程式碼剖析的電腦，您可能會使用連結器參數，或環境變數定義為任何值，再啟動 PGO 檢測程序。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **最佳化**屬性頁。

1. 在 **連結時產生程式碼** 屬性中，選擇**特性指引最佳化-檢測 (/: pginstrument)**。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 請輸入 **/POGOSAFEMODE**到選項**其他選項** 方塊中。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)<br/>
[特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
