---
title: "ICommandSource 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dc8ad34ccce059caca8e86a014622e29c14022ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[ICommandSource::AddCommandHandler](#addcommandhandler)|命令處理常式加入命令來源物件。|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|將一組命令處理常式加入至命令來源物件。|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|將一群使用者介面的命令訊息處理常式加入至命令來源物件。|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|將使用者介面命令訊息處理常式加入至命令來源物件。|  
|[ICommandSource::PostCommand](#postcommand)|公佈訊息，而不需等待處理。|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|命令來源物件中移除的命令處理常式。|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|命令來源物件中移除群組的命令處理常式。|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|命令來源物件中移除一群使用者介面的命令訊息處理常式。|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|命令來源物件中移除的使用者介面命令訊息處理常式。|  
|[ICommandSource::SendCommand](#sendcommand)|傳送訊息並等待其處理後再傳回。|  
  
### <a name="remarks"></a>備註  
 當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 至使用者控制項中的郵件，讓它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。 藉由實作[ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)，讓使用者控制項的參考`ICommandSource`物件。  
  
 請參閱[如何： 新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`ICommandTarget`。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  
  
## <a name="addcommandhandler"></a>ICommandSource::AddCommandHandler
命令處理常式加入命令來源物件。
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數  
`cmdID`  
命令 ID。  
`cmdHandler`  
命令處理常式方法控制代碼。

### <a name="remarks"></a>備註
這個方法會將命令處理常式 cmdHandler 加入命令來源物件，並將此處理常式對應至 cmdID。
請參閱[如何： 新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用 AddCommandHandler 的範例。

## <a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

將一組命令處理常式加入至命令來源物件。
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>參數  
`cmdIDMin`  
命令 ID 範圍的起始索引。
`cmdIDMax`  
命令 ID 範圍結束的索引。
`cmdHandler`  
命令所對應的訊息處理常式方法的控制代碼。
### <a name="remarks"></a>備註
這個方法會將連續的命令 Id 對應至單一訊息處理常式，並將它加入命令來源物件。 這用於一種方法處理一組相關的按鈕。

## <a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler
將一群使用者介面的命令訊息處理常式加入至命令來源物件。
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>參數  
`cmdIDMin`  
命令 ID 範圍的起始索引。
`cmdIDMax`  
命令 ID 範圍結束的索引。
`cmdHandler`  
命令所對應的訊息處理常式方法的控制代碼。

### <a name="remarks"></a>備註
這個方法會將連續的命令 Id 對應至單一使用者介面命令訊息處理常式，並將它加入命令來源物件。 這用於一種方法處理一組相關的按鈕。

## <a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler
將使用者介面命令訊息處理常式加入至命令來源物件。
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>參數
`cmdID`  
命令 ID。  
`cmdUIHandler`  
使用者介面命令訊息處理常式方法控制代碼。

### <a name="remarks"></a>備註
這個方法會將使用者介面命令訊息處理常式 cmdHandler 加入命令來源物件，並將此處理常式對應至 cmdID。

## <a name="postcommand"></a>ICommandSource::PostCommand
公佈訊息，而不需等待處理。
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>參數
`command`  
張貼訊息的命令識別碼。
### <a name="remarks"></a>備註
這個方法以非同步方式將張貼訊息對應至命令所指定的識別碼。 該呼叫 CWnd::PostMessage 將訊息放在視窗的訊息佇列，然後傳回而不需等待處理的訊息對應的視窗。


## <a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler
命令來源物件中移除的命令處理常式。
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>參數
`cmdID`  
命令 ID。
### <a name="remarks"></a>備註
這個方法會移除對應至 cmdID 命令來源物件的命令處理常式。


## <a name="removecommandrangecommandhandler"></a>ICommandSource::RemoveCommandRangeHandler 
命令來源物件中移除群組的命令處理常式。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>參數
`cmdIDMin`  
命令 ID 範圍的起始索引。
`cmdIDMax`  
命令 ID 範圍結束的索引。
### <a name="remarks"></a>備註
這個方法會移除的訊息處理常式，來對應至識別碼指定的命令 cmdIDMin 和 cmdIDMax，從命令來源物件的群組。

## <a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler 
命令來源物件中移除一群使用者介面的命令訊息處理常式。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>參數
`cmdIDMin`  
命令 ID 範圍的起始索引。
`cmdIDMax`  
命令 ID 範圍結束的索引。
### <a name="remarks"></a>備註
這個方法會移除的使用者介面命令訊息處理常式，來對應至識別碼指定的命令 cmdIDMin 和 cmdIDMax，從命令來源物件的群組。

## <a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler 
命令來源物件中移除的使用者介面命令訊息處理常式。
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>參數
`cmdID`  
命令 ID。
### <a name="remarks"></a>備註
這個方法會移除的使用者介面命令訊息處理常式對應至 cmdID 命令來源物件。

## <a name="sendcommand"></a>ICommandSource::SendCommand 
傳送訊息並等待其處理後再傳回。
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>參數
`command`  
命令傳送訊息的識別碼。
### <a name="remarks"></a>備註
這個方法會以同步方式傳送訊息對應至命令所指定的識別碼。 它會呼叫 CWnd::SendMessage 將訊息放在視窗的訊息佇列，並等待，直到該視窗程序處理過訊息後再傳回。
## <a name="see-also"></a>請參閱  
 [如何： 新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget 介面](../../mfc/reference/icommandtarget-interface.md)
