---
title: COleMessageFilter 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 8a6c160a76ae27059238c3e8e26b5bea87a87f7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753827"
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
|[COle 訊息過濾器:COle訊息過濾器](#colemessagefilter)|建構 `COleMessageFilter` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle消息過濾器::開始忙州](#beginbusystate)|將應用程式置於忙狀態。|
|[COle 訊息篩選器::啟用行程對話](#enablebusydialog)|啟用並禁用被調用應用程式忙時出現的對話方塊。|
|[COle 訊息篩選器::啟用不回應對話框](#enablenotrespondingdialog)|啟用並禁用被調用應用程式未回應時出現的對話方塊。|
|[COle訊息過濾器:結束行程](#endbusystate)|終止應用程式的忙狀態。|
|[COle訊息過濾器:開啟訊息掛起](#onmessagepending)|框架調用以在 OLE 調用進行時處理消息。|
|[COle消息過濾器::註冊](#register)|將消息篩選器註冊到 OLE 系統 DLL。|
|[COle 訊息篩選器:撤銷](#revoke)|復原訊息篩選器在 OLE 系統 DLL 中的註冊。|
|[COle消息過濾器::設定忙回覆](#setbusyreply)|確定繁忙的應用程式對 OLE 呼叫的回復。|
|[COle消息篩選器::設定訊息掛起延遲](#setmessagependingdelay)|確定應用程式等待回應 OLE 調用的時間。|
|[COle 訊息篩選器::設定重試回覆](#setretryreply)|確定調用應用程式對繁忙應用程式的回復。|

## <a name="remarks"></a>備註

該`COleMessageFilter`類在可視化編輯伺服器和容器應用程式以及 OLE 自動化應用程式中非常有用。 對於正在調用的伺服器應用程式,此類可用於使應用程式"繁忙",以便取消或稍後重試來自其他容器應用程式的傳入調用。 此類還可用於確定調用應用程式在調用應用程式繁忙時要執行的操作。

常見用法是伺服器應用程式調用[BeginBusyState](#beginbusystate)和[endBusyState,](#endbusystate)當文檔或其他 OLE 可訪問對象被銷毀時,將是危險的。 這些呼叫在[CWinApp 中進行:在使用者介面更新期間處於空閒狀態](../../mfc/reference/cwinapp-class.md#onidle)。

默認情況下,在初始`COleMessageFilter`化應用程式時分配物件。 它可以通過[AfxOleGet 消息篩檢程式](application-control.md#afxolegetmessagefilter)檢索。

這是一個高級類;你很少需要直接使用它。

有關詳細資訊,請參閱文章[「伺服器:實現伺服器](../../mfc/servers-implementing-a-server.md)」。。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COle消息過濾器::開始忙州

調用此函數以開始忙狀態。

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>備註

它與[EndBusyState](#endbusystate)協同工作,以控制應用程式的忙狀態。 函數[SetBusyReply](#setbusyreply)確定應用程式在忙時對調用應用程式的回復。

和`BeginBusyState``EndBusyState`調用增量和遞減,分別一個計數器,用於確定應用程式是否繁忙。 例如,對的`BeginBusyState`兩個調用和一個`EndBusyState`調用仍然會導致忙狀態。 要取消忙狀態,必須調用`EndBusyState`相同`BeginBusyState`次數 的調用。

預設情況下,框架在空閒處理期間進入忙狀態,由[CWinApp 執行::onIdle](../../mfc/reference/cwinapp-class.md#onidle)。 當應用程式正在處理ON_COMMANDUPDATEUI通知時,傳入呼叫將在空閒處理完成後稍後處理。

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COle 訊息過濾器:COle訊息過濾器

建立 `COleMessageFilter` 物件。

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COle 訊息篩選器::啟用行程對話

啟用並禁用忙對話框,該對話框在消息掛起的延遲過期時顯示(請參閱 OLE 調用期間的[SetRetryReply)。](#setretryreply)

```cpp
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>參數

*bEnableBusy*<br/>
指定"忙"對話框是啟用還是禁用。

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COle 訊息篩選器::啟用不回應對話框

啟用並禁用"未回應"對話框,如果 OLE 呼叫期間鍵盤或滑鼠訊息掛起且呼叫超時,則會顯示該對話方塊。

```cpp
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用不回應*<br/>
指定"未回應"對話框是啟用還是禁用。

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COle訊息過濾器:結束行程

調用此函數以結束忙狀態。

```
virtual void EndBusyState();
```

### <a name="remarks"></a>備註

它與[BeginBusyState](#beginbusystate)協同工作,以控制應用程式的忙狀態。 函數[SetBusyReply](#setbusyreply)確定應用程式在忙時對調用應用程式的回復。

和`BeginBusyState``EndBusyState`調用增量和遞減,分別一個計數器,用於確定應用程式是否繁忙。 例如,對的`BeginBusyState`兩個調用和一個`EndBusyState`調用仍然會導致忙狀態。 要取消忙狀態,必須調用`EndBusyState`相同`BeginBusyState`次數 的調用。

預設情況下,框架在空閒處理期間進入忙狀態,由[CWinApp 執行::onIdle](../../mfc/reference/cwinapp-class.md#onidle)。 當應用程式正在處理ON_UPDATE_COMMAND_UI通知時,傳入呼叫將在空閒處理完成後處理。

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COle訊息過濾器:開啟訊息掛起

框架調用以在 OLE 調用進行時處理消息。

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向掛起消息的指標。

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

當呼叫應用程式等待呼叫完成時,框架使用指向暫停訊息的指標呼叫`OnMessagePending`。 默認情況下,框架調度WM_PAINT消息,以便在需要很長時間的調用期間進行視窗更新。

您必須透過除錯註冊來註冊郵件篩選器,然後才能啟動該[篩選器](#register)。

## <a name="colemessagefilterregister"></a><a name="register"></a>COle消息過濾器::註冊

將消息篩選器註冊到 OLE 系統 DLL。

```
BOOL Register();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

除非消息篩選器已註冊到系統 DLL,否則該篩選器無效。 通常,應用程式的初始化代碼註冊應用程式的消息篩選器。 應用程式註冊的任何其他消息篩選器都應在程式終止之前通過調用[Revoke](#revoke)終止。

框架的預設消息篩選器在初始化期間自動註冊,並在終止時撤銷。

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COle 訊息篩選器:撤銷

復原以前由呼叫[註冊執行的註冊](#register)。

```cpp
void Revoke();
```

### <a name="remarks"></a>備註

應在程式終止之前吊銷消息篩選器。

由框架自動創建和註冊的預設消息篩選器也會自動吊銷。

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COle消息過濾器::設定忙回覆

此函數設置應用程式的"忙答覆"。

```cpp
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>參數

*nBusy 回覆*<br/>
枚舉中`SERVERCALL`的值,在 COMPOBJ 中定義。H。 它可以具有以下任一值:

- SERVERCALL_ISHANDLED 應用程式可以接受呼叫,但在處理特定呼叫時可能失敗。

- SERVERCALL_REJECTED應用程式可能永遠無法處理呼叫。

- SERVERCALL_RETRYLATER 應用程式暫時處於無法處理呼叫的狀態。

### <a name="remarks"></a>備註

[BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)函數控制應用程式的忙狀態。

當應用程式忙於調用`BeginBusyState`時,它將回應來自 OLE 系統 DLL 的調用,`SetBusyReply`其值由 最後一 個設置確定。 呼叫應用程式使用此繁忙的答覆來確定要執行的操作。

默認情況下,繁忙的回復是SERVERCALL_RETRYLATER。 此答覆導致調用應用程式儘快重試呼叫。

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COle消息篩選器::設定訊息掛起延遲

確定調用應用程式等待來自被調用應用程式的回應的時間,然後再執行進一步操作。

```cpp
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>參數

*N超時*<br/>
消息掛起延遲的毫秒數。

### <a name="remarks"></a>備註

此函數與[SetRetryReply 協同](#setretryreply)工作。

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COle 訊息篩選器::設定重試回覆

確定調用應用程式在收到來自被調用應用程式的繁忙回應時的操作。

```cpp
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>參數

*nRetry回復*<br/>
重試之間的毫秒數。

### <a name="remarks"></a>備註

當被調用的應用程式指示它處於繁忙狀態時,調用應用程式可能會決定等待伺服器不再繁忙、立即重試或在指定間隔後重試。 它還可能決定完全取消呼叫。

調用方的回應由函數`SetRetryReply`和[SetMessage Pending Delay](#setmessagependingdelay)控制。 `SetRetryReply`確定調用應用程式應在重試給定調用之間等待多長時間。 `SetMessagePendingDelay`確定調用應用程式等待來自伺服器的回應的時間,然後再執行進一步操作。

通常預設值是可以接受的,不需要更改。 框架每隔*nretry 回復*毫秒重試呼叫,直到呼叫通過或消息掛起延遲已過期。 *nRetryReply*的值為 0 指定立即重試,- 1 指定取消呼叫。

當消息掛起延遲過期時,將顯示 OLE"忙對話方塊"(請參閱[COleBusyDialog),](../../mfc/reference/colebusydialog-class.md)以便用戶可以選擇取消或重試呼叫。 呼叫[啟用忙忙對話框](#enablebusydialog)以啟用或禁用此對話框。

當鍵盤或滑鼠消息在呼叫期間掛起且呼叫超時(超過消息掛起延遲)時,將顯示"未回應"對話框。 呼叫[啟用不回應對話框](#enablenotrespondingdialog)以啟用或禁用此對話框。 通常,這種情況表明出現問題,用戶越來越不耐煩。

禁用對話方塊後,當前「重試答覆」始終用於調用繁忙的應用程式。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
