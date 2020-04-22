---
title: 應用程式控制
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 7e18b4504ddbfdd9a4399f33c34c6e6e9900233b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752862"
---
# <a name="application-control"></a>應用程式控制

OLE 要求對應用程式及其物件進行大量控制。 OLE 系統 DLL 必須能夠自動啟動和釋放應用程式,協調物件的生成和修改,等等。 本主題中的函數滿足這些要求。 除了被 OLE 系統 DLL 調用外,應用程式有時還必須調用這些函數。

### <a name="application-control"></a>應用程式控制

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|指示應用程式是否可以結束。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|擷取應用程式的目前訊息篩選器。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|擷取目前使用者控制旗標。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|設置或清除使用者控制標誌。|
|[AfxOleLockApp](#afxolelockapp)|增加框架在應用程式中活動物件數的全域計數。|
|[AfxOleLockControl](#afxolelockcontrol)| 鎖定指定控制項的類工廠。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|聲明框架對應用程式中活動物件數的計數。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 解鎖指定控制件的類工廠。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|在 OLE 系統註冊表中註冊伺服器。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|實現*類型名稱*物件命令的用戶介面。|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp

指示應用程式是否可以結束。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>傳回值

如果應用程式可結束則非零，否則為 0。

### <a name="remarks"></a>備註

如果對應用程式物件有未完成的參考，則不應該結束。 全域函式 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分別會遞增和遞減應用程式物件的參考計數。 這個計數器為非零值時，應用程式不應該結束。 如果計數器是非零值，當使用者從 [系統] 功能表選擇 [關閉]，或從 [檔案] 功能表選擇 [結束] 時，應用程式的主視窗將會隱藏 (不會終結)。 框架在`CFrameWnd::OnClose`中調用此函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGet訊息過濾器

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

### <a name="requirements"></a>需求

**標題**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>阿福奧萊格瑟克拉爾

擷取目前使用者控制旗標。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>傳回值

如果使用者在控制應用程式則為非零；否則為 0。

### <a name="remarks"></a>備註

當使用者具有已明確開啟或建立的新文件時，應用程式是在使用者的控制之下。 如果應用程式不是由 OLE 系統 DLL 啟動，也就是說如果使用者是使用系統殼層啟動應用程式，表示仍然在使用者的控制之下。

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>阿福奧萊塞塞瑟克拉爾

設置或清除使用者控制標誌,這在引用中`AfxOleGetUserCtrl`解釋。

```cpp
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>參數

*bUserCtrl*<br/>
指定是設置還是清除使用者控制標誌。

### <a name="remarks"></a>備註

當使用者創建或載入文檔時,框架呼叫此函數,但當透過間接操作(如從容器應用程式載入嵌入物件)載入或創建文檔時,框架將調用此函數。

如果應用程式中的其他操作應使用戶控制應用程式,請調用此函數。

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>阿FXOlelockApp

增加框架在應用程式中活動物件數的全域計數。

```cpp
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>備註

框架保留應用程式中活動物件數的計數。 和`AfxOleLockApp``AfxOleUnlockApp`函數,分別,增量和遞減此計數。

當使用者嘗試關閉具有活動物件的應用程式(活動物件的計數為非零的應用程式)時,框架會將應用程式從使用者的視圖中隱藏,而不是完全關閉它。 該`AfxOleCanExitApp`函數指示應用程式是否可以終止。

從`AfxOleLockApp`公開 OLE 介面的任何物件調用,如果該物件在用戶端應用程式仍在使用時銷毀該物件是不可取的。 還要在`AfxOleUnlockApp`建構函數中調用`AfxOleLockApp`的任何物件的析構函數中調用。 預設情況下,(`COleDocument`和派生類)會自動鎖定和解鎖應用程式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOle 解鎖應用程式

聲明框架在應用程式中的活動物件的計數。

```cpp
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>備註

有關詳細資訊`AfxOleLockApp`,請參閱。

當活動物件數達到零時,`AfxOleOnReleaseAllObjects`將調用。

### <a name="example"></a>範例

請參閱[AfxOleLockApp](#afxolelockapp)的範例。

### <a name="requirements"></a>需求

**標題**: afxdisp.h

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

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOle註冊伺服器類

此功能允許您在 OLE 系統註冊表中註冊伺服器。

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
引用伺服器的 OLE 類 ID。

*lpszClass 名稱*<br/>
指向包含伺服器物件的類名的字串的指標。

*lpsz短類型名稱*<br/>
指向包含伺服器物件類型的短名稱的字串的指標,如「圖表」。

*lpszLongType 名稱*<br/>
指向包含伺服器物件類型的長名稱的字串的指標,例如「Microsoft Excel 5.0 圖表」。

*nAppType*<br/>
從OLE_APPTYPE枚舉中獲取的值,指定 OLE 應用程式的類型。 可能的值如下：

- OAT_INPLACE_SERVER伺服器具有完整的伺服器用戶介面。

- OAT_SERVER伺服器僅支援嵌入。

- OAT_CONTAINER容器支援指向嵌入的連結。

- OAT_DISPATCH_OBJECT `IDispatch`- 支援物件。

*rglpsz註冊*<br/>
如果找不到鍵的現有值,則指向表示要添加到 OLE 系統註冊表的鍵和值的字串的指標陣列。

*rglpsz 覆寫*<br/>
如果註冊表包含給定鍵的現有值,則指向表示要添加到 OLE 系統註冊表的鍵和值的字串的指標陣列。

### <a name="return-value"></a>傳回值

如果已成功註冊伺服器類,則非零;否則 0。

### <a name="remarks"></a>備註

大多數應用程式都可用於`COleTemplateServer::Register`註冊應用程式的文件類型。 如果應用程式的系統註冊表格式不符合典型模式,則可以使用`AfxOleRegisterServerClass`更多控制項。

註冊表由一組鍵和值組成。 *rglpsz註冊*和*rglpszOverwrite*參數是指向字串的指標陣列,每個參數由鍵和由**NULL**字`'\0'`元 () 分隔的值組成。 每個字串都可以具有可取代的參數,其位置由字串序列 *%1*到 *%5*標籤。

符號填寫如下:

|符號|值|
|------------|-----------|
|%1|類別識別碼為字串|
|%2|類別名稱|
|%3|執行檔路徑|
|%4|短類型名稱|
|%5|長類型名稱|

### <a name="requirements"></a>需求

**標題**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>阿FXOleseteditMenu

實現*類型名稱*物件命令的用戶介面。

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
指向用戶端 OLE 項的指標。

*pMenu*<br/>
指向要更新的功能表物件的指標。

*iMenu 專案*<br/>
要更新的功能表項的索引。

*nIDVerbMin*<br/>
對應於主謂詞的命令 ID。

*nIDVerbMax*<br/>
對應於最後一個謂詞的命令 ID。

*nIDConvert*<br/>
"轉換"選單項的 ID。

### <a name="remarks"></a>備註

如果伺服器僅識別主謂詞,功能表項將成為"動詞*類型物件*",當用戶選擇該命令時發送*nIDVerbMin*命令。 如果伺服器識別多個謂詞,則功能表項將成為 *"typename*物件",並在使用者選擇該命令時顯示列出所有謂詞的子選單。 當使用者從子功能表中選擇動詞時,如果選擇了第一個動詞,則發送*nIDVerbMin;* 如果選擇了第二個謂詞,則發送*nIDVerbMin* = 1,依此類推。 預設`COleDocument`實現會自動處理此功能。

用戶端的應用程式資源腳本 (中必須具有以下語句。RC) 檔案:

**#include\<阿波諾爾克>**

### <a name="requirements"></a>需求

**標題**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOle解鎖控制

解鎖指定控制件的類工廠。

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

如果控件的類工廠已成功解鎖,則非零;否則 0。

### <a name="remarks"></a>備註

控制項與`AfxOleLockControl`鎖定,以便與控制項關聯的動態創建的數據保留在記憶體中。 這可以顯著加快控制項的顯示速度,因為不必在每次顯示控制項時創建和銷毀該控制項。 當您準備終結控制項時，請呼叫 `AfxOleUnlockControl`。

### <a name="example"></a>範例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
