---
title: / POGOSAFEMODE (執行緒安全模式中的執行 PGO) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- POGOSAFEMODE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81392c67b47a0fa90c057ee4295667a054e34498
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377329"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (執行緒安全模式中的執行 PGO)

**/POGOSAFEMODE 選項已被取代，從 Visual Studio 2015 開始**。 使用[/GENPROFILE： 確切](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)和 **/GENPROFILE:NOEXACT**改為選項。 **/POGOSAFEMODE**連結器選項可讓您指定檢測的組建建立使用具備執行緒安全模式設定檔資料擷取期間特性指引最佳化 (PGO) 定型集執行。

## <a name="syntax"></a>語法

> **/POGOSAFEMODE**

## <a name="remarks"></a>備註

特性指引最佳化 (PGO) 的程式碼剖析工作階段有兩個可能的模式：*快速模式*和*安全模式*。 程式碼剖析在快速模式時，它會使用遞增指令來增加資料計數器。 遞增指令較快，但不是執行緒安全。 當程式碼剖析會處於安全模式時，它會使用連鎖遞增指令來增加資料計數器。 這個指令會具有相同的功能，如遞增指令，且具備執行緒安全，但是它變慢。

**/POGOSAFEMODE**選項會設定為使用安全模式檢測的組建。 這個選項只能使用已被取代[/ltcg: pginstrument](ltcg-link-time-code-generation.md)指定，PGO 檢測連結器階段期間。

根據預設，PGO 分析在快速模式下運作。 **/ POGOSAFEMODE**是如果您想要使用安全模式，才需要。

若要執行 PGO 分析在安全模式中，您必須使用 **/GENPROFILE： 確切**（慣用） 或使用環境變數[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md)或連結器參數 **/POGOSAFEMODE**，取決於系統上。 如果您正在執行分析在 x64 電腦，您必須使用連結器參數。 如果您正在執行 x86 程式碼剖析的電腦，您可以使用連結器參數，或者啟動 PGO 檢測程序之前，環境變數定義為任何值。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **最佳化**屬性頁。

1. 在**連結時間產生程式碼**屬性中，選擇**特性指引最佳化-檢測 (/: pginstrument)**。

1. 選取**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入 **/POGOSAFEMODE**選項至**其他選項**方塊。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)<br/>
[特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
