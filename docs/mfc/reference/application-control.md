---
title: 應用程式控制
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 40ac3b6871d13420797279629a2661b22545d1d8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832369"
---
# <a name="application-control"></a>應用程式控制

OLE 需要對應用程式及其物件有大量的控制權。 OLE 系統 Dll 必須能夠自動啟動和發行應用程式、協調其生產和修改物件等等。 本主題中的函數符合這些需求。 除了由 OLE 系統 Dll 呼叫之外，這些函數有時也必須由應用程式呼叫。

### <a name="application-control"></a>應用程式控制

| 名稱 | 描述 |
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|指示應用程式是否可以結束。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|擷取應用程式的目前訊息篩選器。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|擷取目前使用者控制旗標。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|設定或清除使用者控制項旗標。|
|[AfxOleLockApp](#afxolelockapp)|遞增架構在應用程式中使用中物件數目的全域計數。|
|[AfxOleLockControl](#afxolelockcontrol)| 鎖定指定控制項的 class factory。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|減少應用程式中使用中物件數目的架構計數。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 解除鎖定所指定控制項的 class factory。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|在 OLE 系統登錄中註冊伺服器。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|實作為 *typename* 物件命令的使用者介面。|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a> AfxOleCanExitApp

指示應用程式是否可以結束。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>傳回值

如果應用程式可結束則非零，否則為 0。

### <a name="remarks"></a>備註

如果對應用程式物件有未完成的參考，則不應該結束。 全域函式 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分別會遞增和遞減應用程式物件的參考計數。 這個計數器為非零值時，應用程式不應該結束。 如果計數器是非零值，當使用者從 [系統] 功能表選擇 [關閉]，或從 [檔案] 功能表選擇 [結束] 時，應用程式的主視窗將會隱藏 (不會終結)。 架構會在中呼叫這個函數 `CFrameWnd::OnClose` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a> AfxOleGetMessageFilter

擷取應用程式的目前訊息篩選器。

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>傳回值

指向目前訊息篩選器的指標。

### <a name="remarks"></a>備註

就像您會呼叫 `COleMessageFilter` 來存取目前應用程式物件一般，請呼叫這個函式來存取目前的 `AfxGetApp` 衍生物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>規格需求

**標頭**： afxwin.h。h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a> AfxOleGetUserCtrl

擷取目前使用者控制旗標。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>傳回值

如果使用者在控制應用程式則為非零；否則為 0。

### <a name="remarks"></a>備註

當使用者具有已明確開啟或建立的新文件時，應用程式是在使用者的控制之下。 如果應用程式不是由 OLE 系統 DLL 啟動，也就是說如果使用者是使用系統殼層啟動應用程式，表示仍然在使用者的控制之下。

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a> AfxOleSetUserCtrl

設定或清除使用者控制項旗標，此旗標會在的參考中加以說明 `AfxOleGetUserCtrl` 。

```cpp
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>參數

*bUserCtrl*<br/>
指定是否要設定或清除使用者控制項旗標。

### <a name="remarks"></a>備註

當使用者建立或載入檔時，架構會呼叫這個函式，而不是在透過間接動作（例如從容器應用程式載入内嵌物件）載入或建立檔時呼叫這個函數。

如果您應用程式中的其他動作應該讓使用者控制應用程式，請呼叫此函式。

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a> AfxOleLockApp

遞增架構在應用程式中使用中物件數目的全域計數。

```cpp
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>備註

架構會保留應用程式中的作用中物件數目的計數。 `AfxOleLockApp`和 `AfxOleUnlockApp` 函數會分別遞增和遞減此計數。

當使用者嘗試關閉具有使用中物件的應用程式時（使用中物件的計數為非零），此架構會將應用程式從使用者的觀點中隱藏，而不是完全關閉。 此 `AfxOleCanExitApp` 函數會指出應用程式是否可以終止。

`AfxOleLockApp`從任何公開 OLE 介面的物件呼叫，如果在用戶端應用程式仍在使用該物件時，該物件不需要終結。 此外，也請在函式中呼叫的 `AfxOleUnlockApp` 任何物件的析構函數中呼叫 `AfxOleLockApp` 。 根據預設， `COleDocument` (和衍生類別) 會自動鎖定和解除鎖定應用程式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a> AfxOleUnlockApp

遞減架構在應用程式中使用中物件的計數。

```cpp
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>備註

`AfxOleLockApp`如需詳細資訊，請參閱。

當使用中物件的數目到達零時， `AfxOleOnReleaseAllObjects` 會呼叫。

### <a name="example"></a>範例

請參閱 [AfxOleLockApp](#afxolelockapp)的範例。

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

鎖定指定控制項的 Class Factory，以便動態建立與記憶體中保留之控制項相關聯的資料。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>參數

*Clsid*<br/>
控制項的唯一類別 ID。

*lpszProgID*<br/>
控制項的唯一程式 ID。

### <a name="return-value"></a>傳回值

如果已順利鎖定控制項的 Class Factory 則為非零值；否則為 0。

### <a name="remarks"></a>備註

這可大幅提升控制項的顯示速度。 例如，當您在對話方塊中建立控制項並使用 `AfxOleLockControl` 鎖定控制項時，就不需要每次在對話方塊顯示或終止時建立和刪除該控制項。 如果使用者重複開啟和關閉對話方塊，鎖定您的控制項可以大幅提升效能。 當您準備終結控制項時，請呼叫 `AfxOleUnlockControl`。

### <a name="example"></a>範例

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a> AfxOleRegisterServerClass

此函式可讓您在 OLE 系統登錄中註冊您的伺服器。

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
伺服器之 OLE 類別識別碼的參考。

*lpszClassName*<br/>
字串的指標，其中包含伺服器物件的類別名稱。

*lpszShortTypeName*<br/>
字串的指標，其中包含伺服器物件類型的簡短名稱，例如「圖表」。

*lpszLongTypeName*<br/>
字串的指標，其中包含伺服器物件類型的完整名稱，例如「Microsoft Excel 5.0 圖表」。

*nAppType*<br/>
取自 OLE_APPTYPE 列舉的值，指定 OLE 應用程式的類型。 可能的值如下：

- OAT_INPLACE_SERVER Server 具有完整的伺服器使用者介面。

- OAT_SERVER 伺服器僅支援內嵌。

- OAT_CONTAINER 容器支援內嵌的連結。

- `IDispatch`支援 OAT_DISPATCH_OBJECT 的物件。

*rglpszRegister*<br/>
字串指標的陣列，如果找不到索引鍵的現有值，則表示要加入至 OLE 系統登錄的索引鍵和值。

*rglpszOverwrite*<br/>
字串指標的陣列，如果登錄包含指定索引鍵的現有值，則表示要加入至 OLE 系統登錄的索引鍵和值。

### <a name="return-value"></a>傳回值

如果成功註冊伺服器類別，則為非零;否則為0。

### <a name="remarks"></a>備註

大部分的應用程式都可以使用 `COleTemplateServer::Register` 來註冊應用程式的檔案類型。 如果您應用程式的系統登錄格式不符合一般模式，您可以使用 `AfxOleRegisterServerClass` 來進行更多控制。

登錄是由一組索引鍵和值所組成。 *RglpszRegister*和*rglpszOverwrite*引數是字串指標的陣列，每個都是由一個索引鍵和一個值（以**Null**字元分隔） ( `'\0'`) 。 每個字串都可以有可替換的參數，其位置會由字元序列 *%1* 到 *%5*標記。

這些符號的填入方式如下：

|符號|值|
|------------|-----------|
|%1|類別識別碼，格式為字串|
|%2|類別名稱|
|%3|可執行檔的路徑|
|%4|簡短類型名稱|
|%5|完整類型名稱|

### <a name="requirements"></a>規格需求

**標頭**： afxdisp.h。h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a> AfxOleSetEditMenu

實作為 *typename* 物件命令的使用者介面。

```cpp
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>參數

*pClient*<br/>
用戶端 OLE 專案的指標。

*pMenu*<br/>
要更新之功能表物件的指標。

*iMenuItem*<br/>
要更新之功能表項目的索引。

*nIDVerbMin*<br/>
對應至主要動詞命令的命令識別碼。

*nIDVerbMax*<br/>
對應到最後一個動詞命令的命令識別碼。

*nIDConvert*<br/>
[轉換] 功能表項目的識別碼。

### <a name="remarks"></a>備註

如果伺服器只辨識主要動詞命令，功能表項目就會變成「動詞 *typename* 物件」，而 *nIDVerbMin* 命令會在使用者選擇命令時傳送。 如果伺服器辨識了數個動詞，則功能表項目會變成「 *typename* 物件」，而當使用者選擇此命令時，會出現一個子功能表，列出所有的動詞命令。 當使用者從子功能表選擇動詞時，如果選擇第一個動詞，則會傳送 *nIDVerbMin* ，如果選擇第二個動詞，則會傳送 *nIDVerbMin* + 1 等等。 預設的 `COleDocument` 執行會自動處理這項功能。

您必須在用戶端的應用程式資源腳本 ( 中具有下列語句。RC) 檔案：

**#include \<afxolecl.rc>**

### <a name="requirements"></a>規格需求

**標頭**： afxole。h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

解除鎖定所指定控制項的 class factory。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>參數

*Clsid*<br/>
控制項的唯一類別 ID。

*lpszProgID*<br/>
控制項的唯一程式 ID。

### <a name="return-value"></a>傳回值

如果已成功解除鎖定控制項的 class factory，則為非零;否則為0。

### <a name="remarks"></a>備註

控制項已被鎖定 `AfxOleLockControl` ，因此與控制項相關聯的動態建立資料仍會保留在記憶體中。 這可能會大幅加速控制項的顯示，因為不需要在每次顯示控制項時都建立和終結控制項。 當您準備終結控制項時，請呼叫 `AfxOleUnlockControl`。

### <a name="example"></a>範例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
