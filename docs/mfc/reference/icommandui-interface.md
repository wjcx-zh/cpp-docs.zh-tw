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
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751317"
---
# <a name="icommandui-interface"></a>ICommandUI 介面

管理用戶介面命令。

## <a name="syntax"></a>語法

```
interface class ICommandUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[icommandui__Check](#check)|將此命令的用戶介面項設置為相應的檢查狀態。|
|[ICommandUI::繼續路由](#continuerouting)|告訴命令路由機制繼續將當前消息路由到處理程序鏈中。|
|[ICommandUI:已啟用](#enabled)|啟用或禁用此命令的用戶介面項。|
|[ICommandUI:ID](#id)|獲取由物件表示的`ICommandUI`使用者介面對象的 ID。|
|[ICommandUI:索引](#index)|獲取由物件表示的`ICommandUI`用戶介面物件的索引。|
|[ICommandUI::收音機](#radio)|將此命令的用戶介面項設置為相應的檢查狀態。|
|[ICommandUI:文字](#text)|設定此指令的用戶介面項的文本。|

## <a name="remarks"></a>備註

此介面提供管理用戶介面命令的方法和屬性。 `ICommandUI`與[CmCmdUI 類](../../mfc/reference/ccmdui-class.md)`ICommandUI`類似,只 不過用於與 .NET 元件互通的 MFC 應用程式。

`ICommandUI`在[iCommandTarget](../../mfc/reference/icommandtarget-interface.md)派生類中ON_UPDATE_COMMAND_UI處理程式中使用。 當應用程式的使用者啟動(選擇或按一下)功能表時,每個功能表項將顯示為已啟用或禁用。 每個功能表命令的目標通過實現ON_UPDATE_COMMAND_UI處理程式來提供此資訊。 對於應用程式中的每個命令使用者介面物件,使用[類嚮導](mfc-class-wizard.md)為每個處理程式創建消息映射條目和函數原型。

有關介面在命令路由中的`ICommandUI`使用方式的詳細資訊,請參閱[如何:將命令路由添加到 Windows 窗體控制件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

有關如何在 MFC 中管理使用者介面命令的詳細資訊,請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI:檢查

將此命令的用戶介面項設置為相應的檢查狀態。

```
property UICheckState Check;
```

## <a name="remarks"></a>備註

此屬性將此命令的用戶介面項設置為相應的檢查狀態。 將「檢查」設定為以下值:

- 0 取消選取
- 1 檢查
- 2 設定不確定

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI::繼續路由

告訴命令路由機制繼續將當前消息路由到處理程序鏈中。

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>備註

這是一個高級成員函數,應與返回 FALSE 的ON_COMMAND_EX處理程式結合使用。 有關詳細資訊,請參閱技術說明 TN006:消息映射。

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI:已啟用

啟用或禁用此命令的用戶介面項。

```
property bool Enabled;
```

## <a name="remarks"></a>備註

此屬性啟用或禁用此命令的用戶介面項。 設置為 TRUE 以啟用專案,FALSE 將其禁用。

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI:ID

獲取 ICommandUI 物件表示的使用者介面物件的 ID。

```
property unsigned int ID;
```

## <a name="remarks"></a>備註

此屬性獲取功能表項、工具列按鈕或 ICommandUI 物件表示的其他使用者介面物件的 ID(句柄)。

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI:索引

獲取由 ICommandUI 物件表示的使用者介面物件的索引。

```
property unsigned int Index;
```

## <a name="remarks"></a>備註

此屬性獲取功能表項、工具列按鈕或 ICommandUI 物件表示的其他使用者介面物件的索引(句柄)。

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::收音機

將此命令的用戶介面項設置為相應的檢查狀態。

```
property bool Radio;
```

## <a name="remarks"></a>備註

此屬性將此命令的用戶介面項設置為相應的檢查狀態。 將「無線電」設置為 TRUE 以啟用該專案;將「無線電」設置為 TRUE,以啟用該專案。否則 FALSE。

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI:文字

設定此指令的用戶介面項的文本。

```
property String^ Text;
```

## <a name="remarks"></a>備註

此屬性設定此命令的使用者介面項的文本。 將文字設定為文字字串句柄。

## <a name="requirements"></a>需求

**標題**:afxwinforms.h(在程式集 atlmfc_lib_mfcmc80.dll 中定義)

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)
