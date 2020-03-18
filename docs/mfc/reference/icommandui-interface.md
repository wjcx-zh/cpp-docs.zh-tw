---
title: ICommandUI 介面
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: a7bb3ab5ed292cef8108e937e67bc9e2ccc1ebce
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421293"
---
# <a name="icommandui-interface"></a>ICommandUI 介面

管理使用者介面命令。

## <a name="syntax"></a>語法

```
interface class ICommandUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[icommandui__Check](#check)|將此命令的使用者介面專案設定為適當的檢查狀態。|
|[ICommandUI::ContinueRouting](#continuerouting)|告訴命令路由機制，繼續將目前的訊息路由傳送至處理常式鏈。|
|[ICommandUI：： Enabled](#enabled)|啟用或停用此命令的使用者介面專案。|
|[ICommandUI：： ID](#id)|取得 `ICommandUI` 物件所表示之使用者介面物件的識別碼。|
|[ICommandUI：： Index](#index)|取得由 `ICommandUI` 物件所表示之使用者介面物件的索引。|
|[ICommandUI：：收音機](#radio)|將此命令的使用者介面專案設定為適當的檢查狀態。|
|[ICommandUI：： Text](#text)|設定此命令之使用者介面專案的文字。|

## <a name="remarks"></a>備註

這個介面提供管理使用者介面命令的方法和屬性。 `ICommandUI` 類似于[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)，不同之處在于 `ICommandUI` 會用於與 .net 元件互通的 MFC 應用程式。

`ICommandUI` 用於[ICommandTarget](../../mfc/reference/icommandtarget-interface.md)衍生類別的 ON_UPDATE_COMMAND_UI 處理常式中。 當應用程式的使用者啟動（選取或按一下）功能表時，每個功能表項目都會顯示為 [已啟用] 或 [已停用]。 每個功能表命令的目標會藉由執行 ON_UPDATE_COMMAND_UI 處理常式來提供這項資訊。 針對應用程式中的每個命令使用者介面物件，使用[類別 Wizard](mfc-class-wizard.md)來為每個處理常式建立訊息對應專案和函式原型。

如需如何在命令路由中使用 `ICommandUI` 介面的詳細資訊，請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

如需如何在 MFC 中管理使用者介面命令的詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="check"></a>ICommandUI：： Check

將此命令的使用者介面專案設定為適當的檢查狀態。
```
property UICheckState Check;
```

## <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 將 [檢查] 設定為下列值：
- 0取消核取
- 1個檢查
- 2設定不定

## <a name="continuerouting"></a>ICommandUI::ContinueRouting

告訴命令路由機制繼續將目前的訊息路由傳送到處理程式鏈。
```
void ContinueRouting();
```

## <a name="remarks"></a>備註

這是應該與傳回 FALSE 的 ON_COMMAND_EX 處理常式搭配使用的 advanced 成員函式。 如需詳細資訊，請參閱技術提示 TN006：訊息對應。

## <a name="enabled"></a>ICommandUI：： Enabled

啟用或停用此命令的使用者介面專案。
```
property bool Enabled;
```

## <a name="remarks"></a>備註

這個屬性會啟用或停用此命令的使用者介面專案。 將 Enabled 設為 TRUE 以啟用此專案，FALSE 會將它停用。

## <a name="id"></a>ICommandUI：： ID

取得 ICommandUI 物件所代表的使用者介面物件識別碼。
```
property unsigned int ID;
```

## <a name="remarks"></a>備註

這個屬性會取得功能表項目、工具列按鈕或 ICommandUI 物件所表示的其他使用者介面物件的識別碼（控制碼）。

## <a name="index"></a>ICommandUI：： Index

取得 ICommandUI 物件所表示之使用者介面物件的索引。
```
property unsigned int Index;
```

## <a name="remarks"></a>備註

這個屬性會取得功能表項目、工具列按鈕或 ICommandUI 物件所表示的其他使用者介面物件的索引（控制碼）。

## <a name="radio"></a>ICommandUI：：收音機

將此命令的使用者介面專案設定為適當的檢查狀態。
```
property bool Radio;
```

## <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 將 [電臺] 設定為 [TRUE] 以啟用專案;否則為 FALSE。

## <a name="text"></a>ICommandUI：： Text

設定此命令之使用者介面專案的文字。
```
property String^ Text;
```

## <a name="remarks"></a>備註

這個屬性會設定此命令之使用者介面專案的文字。 將文字設定為文字字串控制碼。

## <a name="requirements"></a>需求

**Header：** afxwinforms. h （定義于 assembly atlmfc\lib\mfcmifc80.dll）

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)
