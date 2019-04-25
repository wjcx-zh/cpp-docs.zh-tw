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
ms.openlocfilehash: eed7abbbb40c532ad596f683b6ed2c98a0cadf9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322078"
---
# <a name="icommandsource-interface"></a>ICommandSource 介面

管理從命令來源物件傳送至使用者控制項的命令。

## <a name="syntax"></a>語法

```
interface class ICommandSource
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|將命令來源物件中的命令處理常式。|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|將一群命令處理常式加入命令來源物件。|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|將一群使用者介面的命令訊息處理常式，加入命令來源物件。|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|將命令來源物件中的使用者介面命令訊息處理常式。|
|[ICommandSource::PostCommand](#postcommand)|公佈訊息，而不需等待處理。|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|移除的命令來源物件中的命令處理常式。|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|移除的命令來源物件中的一群命令處理常式。|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|移除的命令來源物件中的一群使用者介面的命令訊息處理常式。|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|命令來源物件中移除的使用者介面命令訊息處理常式。|
|[ICommandSource::SendCommand](#sendcommand)|傳送訊息，並等候它傳回之前進行處理。|

### <a name="remarks"></a>備註

當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 訊息至使用者控制項讓它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。 藉由實作[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)，讓使用者控制項的參考`ICommandSource`物件。

請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`ICommandTarget`。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

將命令來源物件中的命令處理常式。
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdHandler*<br/>
命令處理常式方法的處理常式。

### <a name="remarks"></a>備註

這個方法會將命令來源物件的命令處理常式 cmdHandler，並將處理常式對應至 cmdID。
請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用 AddCommandHandler 的範例。

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

將一群命令處理常式加入命令來源物件。
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
*cmdHandler*<br/>
命令對應至訊息處理常式方法的處理常式。
### <a name="remarks"></a>備註

這個方法會將連續範圍的命令 Id 對應至單一訊息處理常式，並將它新增至命令來源物件。 這用來處理使用其中一種方法的一組相關的按鈕。

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

將一群使用者介面的命令訊息處理常式，加入命令來源物件。
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
*cmdHandler*<br/>
命令對應至訊息處理常式方法的處理常式。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令 Id 對應至單一使用者介面命令訊息處理常式，並將它新增至命令來源物件。 這用來處理使用其中一種方法的一組相關的按鈕。

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

將命令來源物件中的使用者介面命令訊息處理常式。
```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdUIHandler*<br/>
使用者介面命令訊息處理常式方法的處理常式。

### <a name="remarks"></a>備註

這個方法會將命令來源物件中的使用者介面命令訊息處理常式 cmdHandler，並將處理常式對應至 cmdID。

## <a name="postcommand"></a> ICommandSource::PostCommand

公佈訊息，而不需等待處理。
```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要張貼之訊息的命令識別碼。
### <a name="remarks"></a>備註

這個方法會以非同步方式張貼訊息對應到命令所指定的識別碼。 它會呼叫 CWnd::PostMessage 視窗的訊息佇列中放置訊息，並傳回而不需等待處理的訊息對應的視窗。

## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

移除的命令來源物件中的命令處理常式。
```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
### <a name="remarks"></a>備註

這個方法會移除對應至 cmdID 命令來源物件的命令處理常式。

## <a name="removecommandrangehandler"></a> ICommandSource::RemoveCommandRangeHandler

移除的命令來源物件中的一群命令處理常式。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
### <a name="remarks"></a>備註

這個方法會移除一群訊息處理常式，對應至 cmdIDMin 和 cmdIDMax、 命令來源物件中的所指定的命令識別碼。

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

移除的命令來源物件中的一群使用者介面的命令訊息處理常式。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
### <a name="remarks"></a>備註

這個方法會移除一群使用者介面命令訊息處理常式，對應至 cmdIDMin 和 cmdIDMax、 命令來源物件中的所指定的命令識別碼。

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

命令來源物件中移除的使用者介面命令訊息處理常式。
```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
### <a name="remarks"></a>備註

這個方法會移除的使用者介面命令訊息處理常式對應至 cmdID 命令來源物件。

## <a name="sendcommand"></a> ICommandSource::SendCommand

傳送訊息，並等候它傳回之前進行處理。
```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要傳送之訊息的命令識別碼。
### <a name="remarks"></a>備註

這個方法會以同步方式傳送訊息對應到命令所指定的識別碼。 它會呼叫 CWnd::SendMessage 視窗的訊息佇列中放置訊息，並等待，直到該視窗程序已傳回之前處理訊息。
## <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)
