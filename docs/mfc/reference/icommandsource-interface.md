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
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356983"
---
# <a name="icommandsource-interface"></a>ICommandSource 介面

管理從命令源物件發送到使用者控制項的命令。

## <a name="syntax"></a>語法

```cpp
interface class ICommandSource
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICommand 來源:新增指令處理程式](#addcommandhandler)|將命令處理程式添加到命令源物件。|
|[ICommand 來源:新增指令來源處理程式](#addcommandrangehandler)|將一組命令處理程式添加到命令源物件。|
|[ICommand 來源:添加命令RangeUIHandler](#addcommandrangeuihandler)|將一組使用者介面命令訊息處理程式添加到命令源物件。|
|[ICommand 來源:新增命令UIHandler](#addcommandrangeuihandler)|將使用者介面命令訊息處理程式添加到命令源物件。|
|[ICommand 來源::PostCommand](#postcommand)|發佈消息,無需等待處理。|
|[ICommand 來源:移除命令處理程式](#removecommandhandler)|從命令來源物件中刪除命令處理程式。|
|[ICommand 來源:移除命令來源處理程式](#removecommandrangehandler)|從命令來源物件中移除一組命令處理程式。|
|[ICommand 來源:刪除命令RangeUIHandler](#removecommandrangeuihandler)|從命令來源物件中刪除一組使用者介面命令訊息處理程式。|
|[ICommand 來源:刪除命令UIHandler](#removecommandrangeuihandler)|從命令來源物件中刪除使用者介面命令訊息處理程式。|
|[ICommand 來源:傳送指令](#sendcommand)|發送消息並等待處理它,然後再返回。|

### <a name="remarks"></a>備註

當您在 MFC 檢視中託管使用者控件時[,CWinFormsView 類](../../mfc/reference/cwinformsview-class.md)會將命令和命令 UI 訊息更新到使用者控制項,以允許它處理 MFC 命令(例如,框架功能表項和工具列按鈕)。 通過實現[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md),您可以為`ICommandSource`使用者提供對 物件的引用。

有關如何使用,請參閱[:將指令路由新增到 Windows 窗體控制 。](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)`ICommandTarget`

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標題**:afxwinforms.h(在程式集 atlmfc_lib_mfcmc80.dll 中定義)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommand 來源:新增指令處理程式

將命令處理程式添加到命令源物件。

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdHandler*<br/>
命令處理程式方法的句柄。

### <a name="remarks"></a>備註

此方法將命令處理程式 cmdHandler 添加到命令源物件,並將處理程式映射到 cmdID。
有關如何使用 AddCommandHandler 的範例,請參閱[:將指令路由新增到 Windows 元件控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommand 來源:新增指令來源處理程式

將一組命令處理程式添加到命令源物件。

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*釐米德明*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
*cmdHandler*<br/>
命令映射到的消息處理程式方法的句柄。

### <a name="remarks"></a>備註

此方法將連續範圍的命令指示映射到單個消息處理程式,並將其添加到命令源物件。 這用於使用一種方法處理一組相關按鈕。

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommand 來源:添加命令RangeUIHandler

將一組使用者介面命令訊息處理程式添加到命令源物件。

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*釐米德明*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。
*cmdHandler*<br/>
命令映射到的消息處理程式方法的句柄。

### <a name="remarks"></a>備註

此方法將連續範圍的命令指示映射到單個使用者介面命令訊息處理程式,並將其添加到命令源物件。 這用於使用一種方法處理一組相關按鈕。

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommand 來源:新增命令UIHandler

將使用者介面命令訊息處理程式添加到命令源物件。

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。
*cmdUIHandler*<br/>
使用者介面命令訊息處理程式方法的句柄。

### <a name="remarks"></a>備註

此方法將使用者介面命令訊息處理程式 cmdHandler 添加到命令源物件,並將處理程式映射到 cmdID。

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommand 來源::PostCommand

發佈消息,無需等待處理。

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*命令*<br/>
要過帳的消息的命令 ID。

### <a name="remarks"></a>備註

此方法非同步發布映射到命令指定的 ID 的消息。 它調用 CWnd::PostMessage 將消息放在視窗的消息佇列中,然後返回而不等待相應的視窗來處理消息。

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommand 來源:移除命令處理程式

從命令來源物件中刪除命令處理程式。

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

此方法從命令源物件中刪除映射到 cmdID 的命令處理程式。

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommand 來源:移除命令來源處理程式

從命令來源物件中移除一組命令處理程式。

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*釐米德明*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

### <a name="remarks"></a>備註

此方法從命令源物件中刪除一組訊息處理程式,這些處理程式映射到 cmdIDMin 和 cmdIDMax 指定的命令 ID。

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommand 來源:刪除命令RangeUIHandler

從命令來源物件中刪除一組使用者介面命令訊息處理程式。

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*釐米德明*<br/>
命令 ID 範圍的開頭索引。
*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

### <a name="remarks"></a>備註

此方法從命令源物件中刪除一組使用者介面命令訊息處理程式,這些處理程式映射到 cmdIDMin 和 cmdIDMax 指定的命令 ID。

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommand 來源:刪除命令UIHandler

從命令來源物件中刪除使用者介面命令訊息處理程式。

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

此方法從命令源物件中刪除映射到 cmdID 的使用者介面命令訊息處理程式。

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommand 來源:傳送指令

發送消息並等待處理它,然後再返回。

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*命令*<br/>
要發送的消息的命令 ID。

### <a name="remarks"></a>備註

此方法同步發送映射到指令指定的 ID 的消息。 它調用 CWnd::SendMessage 將消息放在視窗的消息佇列中,並等待該視窗過程處理該消息後再返回。

## <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)
