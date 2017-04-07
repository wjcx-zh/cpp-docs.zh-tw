---
title: "COleMessageFilter 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- COleMessageFilter class
- OLE [C++], managing concurrency
- message filters [C++]
- OLE applications [C++], managing interactions
- OLE messages
- applications [OLE], managing interactions
- messages [C++], OLE
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d91ed300bb6cade5d804fe4a74dfe6cc2e4384fe
ms.lasthandoff: 02/24/2017

---
# <a name="colemessagefilter-class"></a>COleMessageFilter 類別
管理 OLE 應用程式互動所需的並行。  
  
## <a name="syntax"></a>語法  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|建構 `COleMessageFilter` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleMessageFilter::BeginBusyState](#beginbusystate)|將應用程式處於忙碌狀態。|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|啟用和停用 忙碌中被呼叫的應用程式時，會出現的對話方塊。|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|啟用和停用時呼叫的應用程式沒有回應，會出現的對話方塊。|  
|[COleMessageFilter::EndBusyState](#endbusystate)|結束應用程式的忙碌狀態。|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|OLE 呼叫正在進行時，處理訊息的架構所呼叫。|  
|[COleMessageFilter::Register](#register)|訊息篩選條件會向 OLE 系統 Dll。|  
|[COleMessageFilter::Revoke](#revoke)|撤銷具有 OLE 系統 Dll 的訊息篩選器註冊。|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|決定 OLE 呼叫忙碌的應用程式回覆。|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|決定應用程式等待 OLE 呼叫的回應的時間長度。|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|判斷呼叫的應用程式忙碌的應用程式的回覆。|  
  
## <a name="remarks"></a>備註  
 `COleMessageFilter`類別會在視覺化編輯伺服器和容器應用程式，以及 OLE automation 應用程式中很有用。 正在呼叫的伺服器應用程式，這個類別可用來讓應用程式 「 忙碌 」，以便從其他容器應用程式的傳入呼叫取消或稍後重試。 這個類別也可用來判斷呼叫的應用程式呼叫的應用程式忙碌時要採取的動作。  
  
 常見的用法是伺服器應用程式呼叫[BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)時很危險的文件或其他 OLE 可存取物件被終結。 在進行這些呼叫[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)期間更新使用者介面。  
  
 根據預設，`COleMessageFilter`應用程式初始化時，配置給物件。 它可以用來擷取[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
 這是進階的類別。您很少需要直接使用它。  
  
 如需詳細資訊，請參閱文章[伺服器︰ 實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="beginbusystate"></a>COleMessageFilter::BeginBusyState  
 呼叫此函式可開始忙錄狀態。  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>備註  
 可搭配[EndBusyState](#endbusystate)控制應用程式的忙碌狀態。 函式[SetBusyReply](#setbusyreply)判斷為忙碌時呼叫的應用程式的應用程式的回覆。  
  
 `BeginBusyState`和`EndBusyState`呼叫遞增和遞減，分別決定應用程式是否忙碌的計數器。 例如，兩個呼叫`BeginBusyState`和一個呼叫`EndBusyState`仍處於忙碌狀態的結果。 若要取消忙碌狀態，就必須呼叫`EndBusyState`相同次數`BeginBusyState`被呼叫。  
  
 根據預設，架構，請輸入在閒置處理，這會由執行的忙碌狀態[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 雖然應用程式正在處理**ON_COMMANDUPDATEUI**閒置處理完成之後更新版本中，處理連入呼叫的通知。  
  
##  <a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter  
 建立 `COleMessageFilter` 物件。  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog  
 啟用和停用 [忙碌] 對話方塊將訊息擱置延遲時間到期時，會顯示 (請參閱[SetRetryReply](#setretryreply)) OLE 呼叫期間。  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bEnableBusy*  
 指定是否啟用或停用 「 忙碌 」 的對話方塊。  
  
##  <a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog  
 啟用和停用 「 沒有回應 」 對話方塊中，如果鍵盤或滑鼠訊息為擱置中會顯示 OLE 期間的呼叫與呼叫逾時。  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bEnableNotResponding*  
 指定是否啟用或停用 「 沒有回應 」 對話方塊。  
  
##  <a name="endbusystate"></a>COleMessageFilter::EndBusyState  
 呼叫此函式來結束忙錄狀態。  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>備註  
 可搭配[BeginBusyState](#beginbusystate)控制應用程式的忙碌狀態。 函式[SetBusyReply](#setbusyreply)判斷為忙碌時呼叫的應用程式的應用程式的回覆。  
  
 `BeginBusyState`和`EndBusyState`呼叫遞增和遞減，分別決定應用程式是否忙碌的計數器。 例如，兩個呼叫`BeginBusyState`和一個呼叫`EndBusyState`仍處於忙碌狀態的結果。 若要取消忙碌狀態，就必須呼叫`EndBusyState`相同次數`BeginBusyState`被呼叫。  
  
 根據預設，架構，請輸入在閒置處理，這會由執行的忙碌狀態[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 雖然應用程式正在處理`ON_UPDATE_COMMAND_UI`通知，來電閒置處理完成之後處理。  
  
##  <a name="onmessagepending"></a>COleMessageFilter::OnMessagePending  
 OLE 呼叫正在進行時，處理訊息的架構所呼叫。  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 `pMsg`  
 暫止訊息的指標。  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 當呼叫的應用程式正在等待呼叫完成時，架構會呼叫`OnMessagePending`具有暫止訊息的指標。 根據預設，架構會分派`WM_PAINT`訊息，以便進行視窗更新期間呼叫需要較長的時間。  
  
 您必須註冊您的郵件篩選器透過呼叫[註冊](#register)之前可能會成為使用中。  
  
##  <a name="register"></a>COleMessageFilter::Register  
 訊息篩選條件會向 OLE 系統 Dll。  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 訊息篩選條件沒有任何作用，除非它已向系統 Dll。 通常您的應用程式的初始化程式碼會註冊應用程式的訊息篩選條件。 應該撤銷註冊您的應用程式的任何其他訊息篩選條件，才能在程式終止的呼叫所[撤銷](#revoke)。  
  
 架構的預設訊息篩選器會自動在初始化期間註冊及撤銷在終止。  
  
##  <a name="revoke"></a>COleMessageFilter::Revoke  
 撤銷先前註冊的呼叫所執行[註冊](#register)。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>備註  
 程式終止之前，應該撤銷訊息篩選條件。  
  
 預設訊息篩選，建立並由架構自動註冊，也會自動撤銷。  
  
##  <a name="setbusyreply"></a>COleMessageFilter::SetBusyReply  
 此函式會將應用程式的 「 忙碌回覆。 」  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>參數  
 *nBusyReply*  
 介於`SERVERCALL`COMPOBJ 中所定義的列舉。H. 它可以包含下列值之一︰  
  
- **SERVERCALL_ISHANDLED**應用程式可以接受的呼叫，但在處理特定的呼叫可能會失敗。  
  
- **SERVERCALL_REJECTED**應用程式可能會永遠無法處理的呼叫。  
  
- **SERVERCALL_RETRYLATER**應用程式會暫時處於狀態中無法處理呼叫。  
  
### <a name="remarks"></a>備註  
 [BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)函式控制應用程式的忙碌狀態。  
  
 當應用程式發出忙著處理呼叫`BeginBusyState`，呼叫從 OLE 系統 Dll 會以回應由最後一個設定的值`SetBusyReply`。 呼叫的應用程式會使用此忙碌的回覆，判斷要採取的動作。  
  
 根據預設，是忙碌的回覆**SERVERCALL_RETRYLATER**。 此回覆會造成呼叫的應用程式，以儘速重試呼叫。  
  
##  <a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay  
 判斷呼叫的應用程式的回應採取進一步的動作之前被呼叫的應用程式等候的時間長度。  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>參數  
 `nTimeout`  
 訊息擱置的延遲毫秒數。  
  
### <a name="remarks"></a>備註  
 此函式可搭配[SetRetryReply](#setretryreply)。  
  
##  <a name="setretryreply"></a>COleMessageFilter::SetRetryReply  
 從被呼叫的應用程式收到忙碌的回應時，請判斷呼叫應用程式的動作。  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>參數  
 `nRetryReply`  
 重試之間的毫秒數。  
  
### <a name="remarks"></a>備註  
 當被呼叫的應用程式表示忙碌時，呼叫的應用程式可能會決定等候，直到伺服器不再是忙碌中，重試，或在特定時間間隔重試。 它也可以決定完全取消呼叫。  
  
 呼叫者的回應由函式`SetRetryReply`和[SetMessagePendingDelay](#setmessagependingdelay)。 `SetRetryReply`判斷呼叫的應用程式應指定呼叫的重試之間等待的時間。 `SetMessagePendingDelay`決定多久呼叫的應用程式等待伺服器回應之前採取進一步動作。  
  
 通常是預設值是可接受並不需要變更。 架構會重試呼叫每個`nRetryReply`呼叫會在執行或已過期的訊息擱置延遲之前的毫秒。 值為 0，表示`nRetryReply`指定立即重試，而 – 1 指定的呼叫取消。  
  
 訊息擱置延遲時間已過期時，OLE 「 忙碌對話方塊 」 (請參閱[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) 會顯示，讓使用者可以選擇取消，或重試呼叫。 呼叫[EnableBusyDialog](#enablebusydialog)啟用或停用此對話方塊。  
  
 鍵盤或滑鼠訊息已暫止時呼叫，並在呼叫期間已逾時 （超過訊息擱置延遲），「 沒有回應 」 對話方塊隨即出現。 呼叫[EnableNotRespondingDialog](#enablenotrespondingdialog)啟用或停用此對話方塊。 通常這個事務狀態的代表發生錯誤，而且使用者會取得耐。  
  
 對話方塊會停用時，目前 重試回覆 「 是一律用於呼叫忙碌的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)

