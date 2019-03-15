---
title: /MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: ecc30baabdcb60a030418e9643e2fcffe5ba8281
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813262"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)

指定使用者帳戶控制 (UAC) 資訊是否內嵌於程式資訊清單中。

## <a name="syntax"></a>語法

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>參數

*fragment*<br/>
字串，其中包含`level`和`uiAccess`值。 如需詳細資訊，請參閱本主題稍後的 < 備註 > 一節。

*_level*<br/>
其中一個*asInvoker*， *highestAvailable*，或*requireAdministrator*。 AsInvoker 預設值。 如需詳細資訊，請參閱本主題稍後的 < 備註 > 一節。

*_uiAccess*<br/>
**真**如果您想要應用程式略過使用者介面保護層級，並輸入放到桌面上更高權限視窗; 否則即為磁碟機**false**。 預設值為**false**。 設定為 **，則為 true**只對使用者介面協助工具應用程式。

## <a name="remarks"></a>備註

如果您指定多個 /MANIFESTUAC 選項，在命令列上的，輸入的最後一個的優先順序較高。

/MANIFESTUAC:level 的選項如下所示：

- `asInvoker`：應用程式會使用相同的權限啟動它的處理序執行。 應用程式可以提升為較高的權限層級，方法是選取**系統管理員身分執行**。

- highestAvailable:應用程式會使用最高的權限等級，它可以執行。 啟動應用程式的使用者是 Administrators 群組的成員，此選項與 requireAdministrator 相同。 最高可用的權限層級高於的開啟處理序層級時，系統會提示輸入認證。

- requireAdministrator:應用程式會使用系統管理員權限執行。 啟動應用程式的使用者必須是 Administrators 群組的成員。 如果開啟處理序不以系統管理權限執行，系統會提示輸入認證。

您可以使用 /MANIFESTUAC:fragment 選項，在一個步驟中指定的層級和 uiAccess 值。 片段必須以下列形式：

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **資訊清單檔案**屬性頁。

1. 修改**啟用使用者帳戶控制 (UAC)**， **UAC 執行層級**，並**UAC 略過 UI 保護**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
