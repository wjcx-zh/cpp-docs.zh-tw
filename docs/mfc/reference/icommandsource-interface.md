---
title: ICommandSource 介面
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: a57ca6f36546a17b9a35ebea875ff01b43de1332
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445707"
---
# <a name="icommandsource-interface"></a>ICommandSource 介面

管理從命令來源物件傳送到使用者控制項的命令。

## <a name="syntax"></a>語法

```
interface class ICommandSource
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICommandSource：： AddCommandHandler](#addcommandhandler)|將命令處理常式加入至命令來源物件。|
|[ICommandSource：： AddCommandRangeHandler](#addcommandrangehandler)|將一組命令處理常式加入至命令來源物件。|
|[ICommandSource：： AddCommandRangeUIHandler](#addcommandrangeuihandler)|將使用者介面命令訊息處理常式群組新增至命令來源物件。|
|[ICommandSource：： AddCommandUIHandler](#addcommandrangeuihandler)|將使用者介面命令訊息處理常式加入至命令來源物件。|
|[ICommandSource：:P ostCommand](#postcommand)|張貼訊息，而不等候處理。|
|[ICommandSource：： RemoveCommandHandler](#removecommandhandler)|從命令來源物件移除命令處理常式。|
|[ICommandSource：： RemoveCommandRangeHandler](#removecommandrangehandler)|從命令來源物件移除一組命令處理常式。|
|[ICommandSource：： RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|從命令來源物件移除使用者介面命令訊息處理常式群組。|
|[ICommandSource：： RemoveCommandUIHandler](#removecommandrangeuihandler)|從命令來源物件移除使用者介面命令訊息處理常式。|
|[ICommandSource：： SendCommand](#sendcommand)|傳送訊息，並等候它在傳回之前處理。|

### <a name="remarks"></a>備註

當您在 MFC 視圖中裝載使用者控制項時， [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)會將命令和更新命令 UI 訊息傳送至使用者控制項，讓它可以處理 MFC 命令（例如，框架功能表項目和工具列按鈕）。 藉由執行[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)，您可以為使用者控制項提供 `ICommandSource` 物件的參考。

如需如何使用 `ICommandTarget`的範例，請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**Header：** afxwinforms. h （定義于 assembly atlmfc\lib\mfcmifc80.dll）

## <a name="addcommandhandler"></a>ICommandSource：： AddCommandHandler

將命令處理常式加入至命令來源物件。

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdHandler*<br/>
命令處理常式方法的控制碼。

### <a name="remarks"></a>備註

這個方法會將命令處理常式 cmdHandler 新增至命令來源物件，並將處理常式對應至 cmdID。
如需如何使用 AddCommandHandler 的範例，請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

## <a name="addcommandrangehandler"></a>ICommandSource：： AddCommandRangeHandler

將一組命令處理常式加入至命令來源物件。

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。
*cmdIDMax*<br/>
命令識別碼範圍的結束索引。
*cmdHandler*<br/>
訊息處理常式方法的控制碼，其對應至命令。
### <a name="remarks"></a>備註

這個方法會將連續範圍的命令識別碼對應至單一訊息處理常式，並將它新增至命令來源物件。 這是用來處理一組具有一種方法的相關按鈕。

## <a name="addcommandrangeuihandler"></a>ICommandSource：： AddCommandRangeUIHandler

將使用者介面命令訊息處理常式群組新增至命令來源物件。

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。
*cmdIDMax*<br/>
命令識別碼範圍的結束索引。
*cmdHandler*<br/>
訊息處理常式方法的控制碼，其對應至命令。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令識別碼對應至單一使用者介面命令訊息處理常式，並將它新增至命令來源物件。 這是用來處理一組具有一種方法的相關按鈕。

## <a name="addcommanduihandler"></a>ICommandSource：： AddCommandUIHandler

將使用者介面命令訊息處理常式加入至命令來源物件。

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdUIHandler*<br/>
使用者介面命令訊息處理常式方法的控制碼。

### <a name="remarks"></a>備註

這個方法會將使用者介面命令訊息處理常式 cmdHandler 加入至命令來源物件，並將處理常式對應至 cmdID。

## <a name="postcommand"></a>ICommandSource：:P ostCommand

張貼訊息，而不等候處理。

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要張貼之訊息的命令識別碼。
### <a name="remarks"></a>備註

這個方法會以非同步方式張貼對應至命令所指定之識別碼的訊息。 它會呼叫 CWnd：:P ostMessage，將訊息放在視窗的訊息佇列中，然後傳回而不等待對應的視窗處理訊息。

## <a name="removecommandhandler"></a>ICommandSource：： RemoveCommandHandler

從命令來源物件移除命令處理常式。

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
### <a name="remarks"></a>備註

這個方法會從命令來源物件移除對應至 cmdID 的命令處理常式。

## <a name="removecommandrangehandler"></a>ICommandSource：： RemoveCommandRangeHandler

從命令來源物件移除一組命令處理常式。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。
*cmdIDMax*<br/>
命令識別碼範圍的結束索引。
### <a name="remarks"></a>備註

這個方法會從命令來源物件中，移除對應至 cmdIDMin 和 cmdIDMax 所指定命令識別碼的訊息處理常式群組。

## <a name="removecommandrangeuihandler"></a>ICommandSource：： RemoveCommandRangeUIHandler

從命令來源物件移除使用者介面命令訊息處理常式群組。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。
*cmdIDMax*<br/>
命令識別碼範圍的結束索引。
### <a name="remarks"></a>備註

這個方法會從命令來源物件中，移除一組使用者介面命令訊息處理常式，並對應至 cmdIDMin 和 cmdIDMax 所指定的命令識別碼。

## <a name="removecommanduihandler"></a>ICommandSource：： RemoveCommandUIHandler

從命令來源物件移除使用者介面命令訊息處理常式。

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
### <a name="remarks"></a>備註

這個方法會從命令來源物件移除對應至 cmdID 的使用者介面命令訊息處理常式。

## <a name="sendcommand"></a>ICommandSource：： SendCommand

傳送訊息，並等候它在傳回之前處理。

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要傳送之訊息的命令識別碼。
### <a name="remarks"></a>備註

這個方法會以同步方式傳送對應至命令所指定之識別碼的訊息。 它會呼叫 CWnd：： SendMessage 將訊息放在視窗的訊息佇列中，並等到該視窗程式在傳回之前處理訊息。
## <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)
