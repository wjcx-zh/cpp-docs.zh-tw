---
title: /MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 96719c6f6f5359afb03b967524b1f65db6dc664a
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334932"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)

指定使用者帳戶控制 (UAC) 資訊是否內嵌於程式資訊清單中。

## <a name="syntax"></a>語法

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>參數

**`NO`**<br/>
連結器不會將 UAC 資訊內嵌在程式資訊清單中。

*`level`*<br/>
**`level=`** 後面接著、或的其中一個 **`'asInvoker'`** **`'highestAvailable'`** **`'requireAdministrator'`** 。 預設為 **`'asInvoker'`** 。 如需詳細資訊，請參閱[備註](#remarks)一節。

*`uiAccess`*<br/>
**`uiAccess='true'`** 如果您想要讓應用程式略過使用者介面保護層級，並在桌上型電腦上將輸入磁片磁碟機設為更高許可權的視窗，否則為 **`uiAccess='false'`** 。 預設為 **`uiAccess='false'`** 。 **`uiAccess='true'`** 僅針對使用者介面協助工具應用程式，將此引數設定為。

*`fragment`*<br/>
包含和值的字串 *`level`* *`uiAccess`* 。 可以選擇性地括在雙引號中。 如需詳細資訊，請參閱[備註](#remarks)一節。

## <a name="remarks"></a>備註

如果您在 **`/MANIFESTUAC`** 命令列上指定多個選項，則最後一個輸入的會優先使用。

的選項如下所示 **`/MANIFESTUAC:`** _`level`_ ：

- **`level='asInvoker'`**：應用程式會在與啟動它的進程相同的許可權層級上執行。 您可以選取 [以**系統管理員身分執行**]，將應用程式提升至較高的許可權等級。

- **`level='highestAvailable'`**：應用程式會在它可以的最高許可權層級執行。 如果啟動應用程式的使用者是 Administrators 群組的成員，這個選項就會與相同 **`level='requireAdministrator'`** 。 如果最高可用的許可權等級高於開啟進程的層級，系統就會提示您輸入認證。

- **`level='requireAdministrator'`**：應用程式會使用系統管理員許可權來執行。 啟動應用程式的使用者必須是 Administrators 群組的成員。 如果開啟進程未以系統管理許可權執行，系統會提示您輸入認證。

您可以 *`level`* *`uiAccess`* 使用選項，在一個步驟中指定和值 **`/MANIFESTUAC:`** _`fragment`_ 。 片段的格式必須如下：

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

例如：

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性**] [  >  **連結器**  >  **資訊清單**檔案] 屬性頁。

1. 修改 [**啟用使用者帳戶控制（UAC）**]、[ **Uac 執行層級**] 和 [ **uac 略過 UI 保護**] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
