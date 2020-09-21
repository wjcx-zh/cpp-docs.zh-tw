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
ms.openlocfilehash: 0c185e873f526403e86cb5a80f6e0631f8654284
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743434"
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
|[ICommandUI：： ContinueRouting](#continuerouting)|告訴命令路由機制繼續將目前的訊息路由傳送至處理常式的鏈。|
|[ICommandUI：： Enabled](#enabled)|啟用或停用此命令的使用者介面專案。|
|[ICommandUI：： ID](#id)|取得物件所表示之使用者介面物件的識別碼 `ICommandUI` 。|
|[ICommandUI：： Index](#index)|取得物件所表示之使用者介面物件的索引 `ICommandUI` 。|
|[ICommandUI：：選項按鈕](#radio)|將此命令的使用者介面專案設定為適當的檢查狀態。|
|[ICommandUI：： Text](#text)|設定此命令的使用者介面專案文字。|

### <a name="remarks"></a>備註

這個介面會提供管理使用者介面命令的方法和屬性。 `ICommandUI` 與 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)類似，不同之處在于它 `ICommandUI` 會用於與 .net 元件互通的 MFC 應用程式。

`ICommandUI` 在 [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)衍生類別的 ON_UPDATE_COMMAND_UI 處理常式中使用。 當應用程式的使用者啟動時 (選取或按一下功能表) ，每個功能表項目會顯示為 [已啟用] 或 [已停用]。 每個功能表命令的目標都會藉由執行 ON_UPDATE_COMMAND_UI 處理常式來提供這項資訊。 針對應用程式中的每個命令使用者介面物件，使用 [ [類別] Wizard](mfc-class-wizard.md) 建立每個處理常式的訊息對應專案和函式原型。

如需有關如何 `ICommandUI` 在命令路由中使用介面的詳細資訊，請參閱 [如何：將命令路由加入至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

如需如何在 MFC 中管理使用者介面命令的詳細資訊，請參閱 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="icommanduicheck"></a><a name="check"></a> ICommandUI：： Check

將此命令的使用者介面專案設定為適當的檢查狀態。

```
property UICheckState Check;
```

### <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 將檢查設定為下列值：

- 0取消核取
- 1個檢查
- 2設定不定

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a> ICommandUI：： ContinueRouting

告訴命令路由機制繼續將目前的訊息路由傳送至處理常式的鏈。

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是要與傳回 FALSE 的 ON_COMMAND_EX 處理常式搭配使用的 advanced 成員函式。 如需詳細資訊，請參閱 Technical Note TN006： Message Map。

## <a name="icommanduienabled"></a><a name="enabled"></a> ICommandUI：： Enabled

啟用或停用此命令的使用者介面專案。

```
property bool Enabled;
```

### <a name="remarks"></a>備註

這個屬性會啟用或停用此命令的使用者介面專案。 將 [已啟用] 設定為 [TRUE] 以啟用專案，FALSE 則停用。

## <a name="icommanduiid"></a><a name="id"></a> ICommandUI：： ID

取得 ICommandUI 物件所代表的使用者介面物件識別碼。

```
property unsigned int ID;
```

### <a name="remarks"></a>備註

這個屬性會取得識別碼， (功能表項目、工具列按鈕或 ICommandUI 物件所代表之其他使用者介面物件的控制碼) 。

## <a name="icommanduiindex"></a><a name="index"></a> ICommandUI：： Index

取得 ICommandUI 物件所代表的使用者介面物件的索引。

```
property unsigned int Index;
```

### <a name="remarks"></a>備註

這個屬性會取得索引， (功能表項目、工具列按鈕或 ICommandUI 物件所代表之其他使用者介面物件的控制碼) 。

## <a name="icommanduiradio"></a><a name="radio"></a> ICommandUI：：選項按鈕

將此命令的使用者介面專案設定為適當的檢查狀態。

```
property bool Radio;
```

### <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 將 [無線電] 設定為 [TRUE] 以啟用專案;否則為 FALSE。

## <a name="icommanduitext"></a><a name="text"></a> ICommandUI：： Text

設定此命令的使用者介面專案文字。

```
property String^ Text;
```

### <a name="remarks"></a>備註

這個屬性會設定此命令之使用者介面專案的文字。 將文字設定為文字字串控制碼。

## <a name="requirements"></a>規格需求

**標頭：** afxwinforms (定義于元件 atlmfc\lib\mfcmifc80.dll) 

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)
