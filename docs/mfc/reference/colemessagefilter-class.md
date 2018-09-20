---
title: COleMessageFilter 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
dev_langs:
- C++
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 585044a5da8ca3ce8b2650801558b19bf1d5ef59
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427793"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter 類別

管理 OLE 應用程式互動所需的並行。

## <a name="syntax"></a>語法

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|建構 `COleMessageFilter` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|會導致應用程式處於忙碌狀態。|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|啟用和停用時呼叫的應用程式忙碌中，會顯示對話方塊。|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|啟用和停用時呼叫的應用程式沒有回應，會出現的對話方塊。|
|[COleMessageFilter::EndBusyState](#endbusystate)|應用程式的忙碌狀態就會終止。|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|由架構呼叫以處理訊息 OLE 呼叫正在進行時。|
|[COleMessageFilter::Register](#register)|向 OLE 系統 Dll 中的訊息篩選條件。|
|[COleMessageFilter::Revoke](#revoke)|撤銷向 OLE 系統 Dll 的訊息篩選條件的註冊。|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|決定 OLE 呼叫忙碌的應用程式的回覆。|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|判斷應用程式與 OLE 呼叫的回應之間的等待時間長度。|
|[COleMessageFilter::SetRetryReply](#setretryreply)|判斷呼叫的應用程式忙碌的應用程式的回覆。|

## <a name="remarks"></a>備註

`COleMessageFilter`類別是用於視覺化編輯伺服器和容器應用程式，以及 OLE automation 應用程式。 對於呼叫的伺服器應用程式，這個類別可用來讓應用程式 「 忙碌 」，以便從其他容器應用程式的連入呼叫取消或稍後重試。 這個類別也可用來判斷呼叫的應用程式忙碌時，呼叫的應用程式所採取的動作。

常見的用法是針對伺服器應用程式，以呼叫[BeginBusyState](#beginbusystate)並[EndBusyState](#endbusystate)時相當危險的文件或其他 OLE 可存取物件，也將被銷毀。 在進行這些呼叫[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)在使用者介面更新期間。

根據預設，`COleMessageFilter`初始化應用程式時，會配置物件。 可以使用擷取[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。

這是進階的類別;您很少需要直接使用它。

如需詳細資訊，請參閱文章[伺服器： 實作伺服器](../../mfc/servers-implementing-a-server.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState

呼叫此函式以開始忙錄狀態。

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>備註

它可搭配[EndBusyState](#endbusystate)來控制應用程式的忙碌狀態。 此函式[SetBusyReply](#setbusyreply)決定為忙碌時，呼叫應用程式的應用程式的回覆。

`BeginBusyState`和`EndBusyState`呼叫遞增和遞減，分別計數器來判斷應用程式是否忙碌中。 例如，兩個呼叫來`BeginBusyState`和一個呼叫`EndBusyState`仍處於忙碌狀態的結果。 若要取消忙錄狀態，就必須呼叫`EndBusyState`相同次數`BeginBusyState`已呼叫。

根據預設，架構，請輸入在閒置處理，這會由執行期間的忙錄狀態[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 雖然應用程式正在處理 ON_COMMANDUPDATEUI 通知，傳入的呼叫會在閒置處理完成後更新版本中，處理。

##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter

建立 `COleMessageFilter` 物件。

```
COleMessageFilter();
```

##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog

啟用和停用忙碌的對話方塊中，這在訊息擱置延遲時間到期時顯示 (請參閱[SetRetryReply](#setretryreply)) OLE 呼叫期間。

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>參數

*bEnableBusy*<br/>
指定是否啟用或停用 「 忙碌 」 的對話方塊。

##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog

啟用和停用 「 沒有回應 」 的對話方塊中，如果鍵盤或滑鼠訊息處於暫止狀態就會顯示 OLE 期間呼叫與呼叫已逾時。

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>參數

*bEnableNotResponding*<br/>
指定是否啟用或停用 「 沒有回應 」 的對話方塊。

##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState

呼叫此函式來結束忙錄狀態。

```
virtual void EndBusyState();
```

### <a name="remarks"></a>備註

它可搭配[BeginBusyState](#beginbusystate)來控制應用程式的忙碌狀態。 此函式[SetBusyReply](#setbusyreply)決定為忙碌時，呼叫應用程式的應用程式的回覆。

`BeginBusyState`和`EndBusyState`呼叫遞增和遞減，分別計數器來判斷應用程式是否忙碌中。 例如，兩個呼叫來`BeginBusyState`和一個呼叫`EndBusyState`仍處於忙碌狀態的結果。 若要取消忙錄狀態，就必須呼叫`EndBusyState`相同次數`BeginBusyState`已呼叫。

根據預設，架構，請輸入在閒置處理，這會由執行期間的忙錄狀態[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 應用程式正在處理 ON_UPDATE_COMMAND_UI 通知，而閒置處理完成後，就是會處理連入呼叫。

##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending

由架構呼叫以處理訊息 OLE 呼叫正在進行時。

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
暫止訊息指標。

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

當呼叫的應用程式正在等候完成的呼叫時，架構會呼叫`OnMessagePending`暫止訊息的指標。 根據預設，架構會分派 WM_PAINT 訊息，以便進行 windows 更新期間呼叫需要較長的時間。

您必須註冊您的訊息篩選器，透過呼叫[註冊](#register)之前可能會成為作用中。

##  <a name="register"></a>  COleMessageFilter::Register

向 OLE 系統 Dll 中的訊息篩選條件。

```
BOOL Register();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

訊息篩選條件沒有任何作用，除非它向系統 Dll。 通常您的應用程式初始化程式碼會註冊應用程式的訊息篩選條件。 註冊您的應用程式的任何其他訊息篩選器應撤銷，才能在程式終止的呼叫所[撤銷](#revoke)。

架構的預設訊息篩選是自動註冊在初始化期間，並在終止撤銷。

##  <a name="revoke"></a>  COleMessageFilter::Revoke

撤銷先前呼叫所執行的登錄[註冊](#register)。

```
void Revoke();
```

### <a name="remarks"></a>備註

程式終止之前，應該撤銷訊息篩選條件。

預設訊息篩選器，會建立，並由架構自動註冊，也會自動撤銷。

##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply

此函式會將應用程式的 「 忙碌回覆。 」

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>參數

*nBusyReply*<br/>
值，以從`SERVERCALL`COMPOBJ 中定義的列舉。H. 它可以包含下列值之一：

- SERVERCALL_ISHANDLED 應用程式可以接受呼叫，但在處理特定的呼叫可能會失敗。

- SERVERCALL_REJECTED 應用程式可能會永遠無法處理呼叫。

- SERVERCALL_RETRYLATER 應用程式暫時處於無法裡面處理呼叫的狀態。

### <a name="remarks"></a>備註

[BeginBusyState](#beginbusystate)並[EndBusyState](#endbusystate)函式會控制應用程式的忙碌狀態。

當應用程式已藉由呼叫忙碌`BeginBusyState`，它會回應呼叫 OLE 系統 Dll 從取決於最後一項設定的值`SetBusyReply`。 呼叫的應用程式會使用這個忙線中的回覆，以判斷要採取的動作。

根據預設，忙碌的回覆是 SERVERCALL_RETRYLATER。 此回覆會導致呼叫的應用程式，以儘速重試呼叫。

##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay

判斷呼叫的應用程式呼叫的應用程式，再採取進一步動作的回應的等候時間長度。

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>參數

*nTimeout*<br/>
訊息擱置延遲的毫秒數。

### <a name="remarks"></a>備註

此函式搭配運作[SetRetryReply](#setretryreply)。

##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply

從被呼叫的應用程式接收忙碌回應時，請判斷呼叫應用程式的動作。

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>參數

*nRetryReply*<br/>
重試之間的毫秒數。

### <a name="remarks"></a>備註

當被呼叫的應用程式表示它很忙碌時，呼叫的應用程式可能會決定等候，直到伺服器不再忙碌中，重試，或指定的間隔之後重試。 它也可以決定將完全取消呼叫。

呼叫端的回應會受到函式`SetRetryReply`並[SetMessagePendingDelay](#setmessagependingdelay)。 `SetRetryReply` 判斷呼叫的應用程式應該呼叫指定的重試之間等待的時間。 `SetMessagePendingDelay` 決定多久呼叫的應用程式等待來自伺服器的回應，再採取進一步動作。

通常預設值是可接受的而且不需要變更。 此架構會重試呼叫每個*nRetryReply*直到呼叫會通過，或已過期的訊息擱置延遲 （毫秒)。 值為 0，表示*nRetryReply*指定立即重試，以及-1 指定的呼叫取消。

當訊息擱置的延遲已過期，OLE 「 忙碌對話方塊 」 (請參閱[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) 會顯示，讓使用者可以選擇取消，或重試呼叫。 呼叫[EnableBusyDialog](#enablebusydialog)啟用或停用此對話方塊。

當鍵盤或滑鼠訊息已暫止期間呼叫與呼叫已逾時 （超過訊息擱置的延遲），「 沒有回應 」 的對話方塊隨即出現。 呼叫[EnableNotRespondingDialog](#enablenotrespondingdialog)啟用或停用此對話方塊。 通常這個事務狀態的表示，發生錯誤，而且使用者即將耐心不足。

對話方塊會停用時，目前 [重試回覆] 會永遠用於呼叫忙碌的應用程式。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
