---
title: COleControlContainer 類別
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 3aa2515b1731eafcb5e3bcfa22a56ebbc1cdfdfb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504331"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer 類別

做為 ActiveX 控制項的控制項容器。

## <a name="syntax"></a>語法

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|建構 `COleControlContainer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|建立容器所裝載的控制項網站。|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|通知所有裝載的控制項環境屬性已變更。|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按鈕控制項。|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|選取群組的指定選項按鈕。|
|[COleControlContainer::CreateControl](#createcontrol)|建立主控的 ActiveX 控制項。|
|[COleControlContainer::CreateOleFont](#createolefont)|建立 OLE 字型。|
|[COleControlContainer::FindItem](#finditem)|傳回指定之控制項的自訂網站。|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|判斷控制網站是否接受事件。|
|[COleControlContainer::GetAmbientProp](#getambientprop)|抓取指定的環境屬性。|
|[COleControlContainer::GetDlgItem](#getdlgitem)|抓取指定的對話方塊控制項。|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|抓取指定之對話方塊控制項的值。|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|抓取指定之對話方塊控制項的標題。|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|判斷容器是否處理 WM_SETFOCUS 的訊息。|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|處理傳送至無視窗控制項的訊息。|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|決定指定按鈕的狀態。|
|[COleControlContainer::OnPaint](#onpaint)|呼叫以重新繪製容器的一部分。|
|[COleControlContainer::OnUIActivate](#onuiactivate)|當控制項即將就地啟用時呼叫。|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|當即將停用控制項時呼叫。|
|[COleControlContainer::ScrollChildren](#scrollchildren)|由架構在從子視窗接收捲軸訊息時呼叫。|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|將訊息傳送至指定的控制項。|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|設定指定之控制項的值。|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|設定指定控制項的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|容器的背景色彩。|
|[COleControlContainer::m_crFore](#m_crfore)|容器的前景色彩。|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|支援的控制項網站清單。|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|託管的無視窗控制項數目。|
|[COleControlContainer::m_pOleFont](#m_polefont)|自訂控制項網站之 OLE 字型的指標。|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|「Capture 控制」網站的指標。|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|目前有輸入焦點之控制項的指標。|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|目前已啟用之控制項的指標。|
|[COleControlContainer::m_pWnd](#m_pwnd)|執行控制項容器之視窗的指標。|
|[COleControlContainer::m_siteMap](#m_sitemap)|網站地圖。|

## <a name="remarks"></a>備註

這是藉由提供一或多個 ActiveX 控制項網站的支援 (由`COleControlSite`所執行) 來完成。 `COleControlContainer`完整執行[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe)和[IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer)介面, 讓內含的 ActiveX 控制項能夠以就地專案的方式來履行其資格。

此類別通常會與`COccManager`搭配使用, 並`COleControlSite`使用一或多個 activex 控制項的自訂網站來執行自訂的 activex 控制項容器。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>需求

**標頭:** afxocc。h

##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

由架構呼叫以建立和附加控制項網站。

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
          `CWnd` 物件的指標。

*nIDC*<br/>
要附加之控制項的識別碼。

### <a name="remarks"></a>備註

如果您想要自訂此進程, 請覆寫此函式。

> [!NOTE]
>  如果您要以靜態方式連結至 MFC 程式庫, 請使用此函式的第一種形式。 如果您要動態連結至 MFC 程式庫, 請使用第二個表單。

##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

通知所有裝載的控制項環境屬性已變更。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
要變更之環境屬性的分派識別碼。

### <a name="remarks"></a>備註

當環境屬性變更值時, 架構會呼叫這個函式。 覆寫此函式以自訂此行為。

##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

修改按鈕的目前狀態。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
要修改之按鈕的識別碼。

*nCheck*<br/>
指定按鈕的狀態。 可以是下列其中一項：

- BST_CHECKED 會將按鈕狀態設定為 [已核取]。

- BST_INDETERMINATE 會將按鈕狀態設定為灰色, 表示不確定的狀態。 只有當按鈕具有 BS_3STATE 或 BS_AUTO3STATE 樣式時, 才使用此值。

- BST_UNCHECKED 會將按鈕狀態設定為 [已清除]。

##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

選取群組中的指定選項按鈕, 並清除群組中其餘的按鈕。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>參數

*nIDFirstButton*<br/>
指定群組中第一個選項按鈕的識別碼。

*nIDLastButton*<br/>
指定群組中最後一個選項按鈕的識別碼。

*nIDCheckButton*<br/>
指定要檢查之選項按鈕的識別碼。

##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

建構 `COleControlContainer` 物件。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
控制項容器之父視窗的指標。

### <a name="remarks"></a>備註

成功建立物件之後, 請使用呼叫來`AttachControlSite`新增自訂控制項網站。

##  <a name="createcontrol"></a>COleControlContainer:: CreateControl

建立由指定`COleControlSite`物件主控的 ActiveX 控制項。

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>參數

*pWndCtrl*<br/>
代表控制項的視窗物件指標。

*clsid*<br/>
控制項的唯一類別 ID。

*lpszWindowName*<br/>
要在控制項中顯示的文字指標。 設定控制項的 [標題] 或 [Text] 屬性的值 (如果有的話)。 如果是 Null, 則不會變更控制項的 Caption 或 Text 屬性。

*dwStyle*<br/>
視窗樣式。 可用的樣式列在 [**備註**] 區段底下。

*rect*<br/>
指定控制項的大小和位置。 它可以`CRect`是物件`RECT`或結構。

*nID*<br/>
指定控制項的子視窗識別碼。

*pPersist*<br/>
的指標, `CFile`其中包含控制項的持續狀態。 預設值為 Null, 表示控制項會自行初始化, 而不會從任何持續性儲存體還原其狀態。 如果不是 Null, 它應該是衍生物件的`CFile`指標, 其中包含控制項的持續性資料 (以資料流程或儲存體的形式)。 這項資料可能已儲存在用戶端先前的啟用中。 可以包含其他資料, 但在`CreateControl`呼叫時, 必須將其讀寫指標設定為持續性資料的第一個位元組。 `CFile`

*bStorage*<br/>
指出*pPersist*中的資料是否應解讀為`IStorage`或`IStream`資料。 如果*pPersist*中的資料是儲存體, 則*BSTORAGE*應為 TRUE。 如果*pPersist*中的資料是資料流程, *BSTORAGE*應該是 FALSE。 預設值為 FALSE。

*bstrLicKey*<br/>
選擇性的授權金鑰資料。 只有在建立需要執行時間授權金鑰的控制項時, 才需要此資料。 如果控制項支援授權, 您必須提供授權金鑰, 才能成功建立控制項。 預設值為 Null。

*ppNewSite*<br/>
將主控所建立控制項之現有控制網站的指標。 預設值為 Null, 表示將自動建立新的控制項網站, 並將其附加至新的控制項。

*ppt*<br/>
`POINT`結構的指標, 其中包含控制項的左上角。 控制項的大小取決於*psize*的值。 *Ppt*和*psize*值是選擇性的方法, 可指定控制項的大小和位置。

*psize*<br/>
`SIZE`結構的指標, 其中包含控制項的大小。 左上角是由*ppt*的值決定。 *Ppt*和*psize*值是選擇性的方法, 可指定控制項的大小和位置。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

僅支援`CreateControl`部分的 Windows *dwStyle*旗標:

- WS_VISIBLE 會建立一開始顯示的視窗。 如果您想要立即顯示控制項 (例如一般視窗), 則為必要。

- WS_DISABLED 會建立一開始停用的視窗。 停用的視窗無法接收使用者的輸入。 如果控制項具有已啟用的屬性, 則可以設定。

- WS_BORDER 會建立具有細線條框線的視窗。 如果控制項具有 BorderStyle 屬性, 則可以設定。

- WS_GROUP 指定控制項群組的第一個控制項。 使用者可以使用方向鍵, 將鍵盤焦點從群組中的一個控制項變更為下一個。 在第一個控制項屬於相同群組之後, 以 WS_GROUP 樣式定義的所有控制項。 下一個具有 WS_GROUP 樣式的控制項會結束群組, 並啟動下一個群組。

- WS_TABSTOP 指定當使用者按下 TAB 鍵時, 可接收鍵盤焦點的控制項。 按 TAB 鍵會將鍵盤焦點變更為 WS_TABSTOP 樣式的下一個控制項。

使用第二個多載來建立預設大小的控制項。

##  <a name="createolefont"></a>COleControlContainer::CreateOleFont

建立 OLE 字型。

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
控制項容器所要使用之字型的指標。

##  <a name="finditem"></a>COleControlContainer::FindItem

尋找裝載指定專案的自訂網站。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
要尋找之專案的識別碼。

### <a name="return-value"></a>傳回值

指定專案之自訂網站的指標。

##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

判斷容器是否會忽略附加的控制網站中的事件或接受它們。

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>參數

*bFreeze*<br/>
如果將處理事件, 則為非零值;否則為0。

### <a name="remarks"></a>備註

> [!NOTE]
>  控制項容器要求時, 不一定要停止引發事件。 它可以繼續引發, 但控制項容器將會忽略所有後續事件。

##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp

抓取指定環境屬性的值。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>參數

*pSite*<br/>
將從中抓取環境屬性的控制網站指標。

*dispid*<br/>
所需環境屬性的分派識別碼。

*pVarResult*<br/>
環境屬性值的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem

抓取對話方塊或其他視窗中指定之控制項或子視窗的指標。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
要取出之對話方塊專案的識別碼。

*phWnd*<br/>
指定對話方塊專案之視窗物件的控制碼指標。

### <a name="return-value"></a>傳回值

對話方塊專案視窗的指標。

##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

抓取指定控制項的已翻譯文字值。

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別碼。

*lpTrans*<br/>
接收函式成功/失敗值的布林變數指標 (TRUE 表示成功, FALSE 表示失敗)。

*bSigned*<br/>
指定函式是否應在開頭檢查減號的文字, 如果找到, 則傳回帶正負號的整數值。 如果*bSigned*參數為 TRUE, 則指定要抓取的值是帶正負號的整數值, 並將傳回值轉換成**int**類型。 若要取得延伸錯誤資訊, 請呼叫[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="return-value"></a>傳回值

如果成功, *lpTrans*所指向的變數會設定為 TRUE, 而傳回值就是控制項文字的轉譯值。

如果函式失敗, *lpTrans*所指向的變數會設定為 FALSE, 而傳回值則為零。 請注意, 因為零是可能的轉譯值, 所以傳回值零本身不會指出失敗。

如果*lpTrans*為 Null, 則函數不會傳回成功或失敗的相關資訊。

### <a name="remarks"></a>備註

函式會藉由去除文字開頭的任何額外空格, 然後轉換十進位數, 來轉譯抓取的文字。 當函式到達文字結尾或遇到非數值字元時, 函式會停止翻譯。

如果轉譯的值大於 INT_MAX (適用于帶正負號的數位) 或 UINT_MAX (不帶正負號的數位), 則此函式會傳回零。

##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

抓取指定控制項的文字。

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別碼。

*lpStr*<br/>
控制項文字的指標。

*nMaxCount*<br/>
指定要複製到*lpStr*所指向之緩衝區的字串長度上限 (以字元為單位)。 如果字串長度超過限制, 則字串會被截斷。

### <a name="return-value"></a>傳回值

如果函式成功, 則傳回值會指定複製到緩衝區的字元數, 不包括終止的 null 字元。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊, 請呼叫[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

判斷容器是否處理 WM_SETFOCUS 的訊息。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>傳回值

如果容器處理 WM_SETFOCUS 的訊息, 則為非零值;否則為零。

##  <a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

處理無視窗控制項的視窗訊息。

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>參數

*message*<br/>
視窗訊息的識別碼 (由 Windows 提供)。

*wParam*<br/>
訊息的參數;由 Windows 提供。 指定其他訊息特定資訊。 此參數的內容取決於*message*參數的值。

*lParam*<br/>
訊息的參數;由 Windows 提供。 指定其他訊息特定資訊。 此參數的內容取決於*message*參數的值。

*plResult*<br/>
Windows 結果碼。 指定訊息處理的結果, 並根據傳送的訊息而定。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

覆寫此函式以自訂無視窗控制訊息的處理。

##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

決定指定按鈕的狀態。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

從使用 BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON 或 BS_3STATE 樣式所建立的按鈕傳回的值。 可以是下列其中一項：

- 已核取 [BST_CHECKED] 按鈕。

- BST_INDETERMINATE 按鈕呈現灰色, 表示不確定狀態 (只有在按鈕具有 BS_3STATE 或 BS_AUTO3STATE 樣式時才適用)。

- 已清除 [BST_UNCHECKED] 按鈕。

### <a name="remarks"></a>備註

如果按鈕是三個狀態的控制項, 則成員函式會判斷其為灰色、已核取, 或兩者皆非。

##  <a name="m_crback"></a>COleControlContainer::m_crBack

容器的背景色彩。

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>COleControlContainer::m_crFore

容器的前景色彩。

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

容器主控的控制網站清單。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

控制項容器主控的無視窗控制項數目。

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont

自訂控制項網站之 OLE 字型的指標。

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

「Capture 控制」網站的指標。

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

目前具有輸入焦點之控制網站的指標。

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

就地啟用之控制網站的指標。

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd

與容器相關聯之 window 物件的指標。

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap

網站地圖。

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>COleControlContainer:: OnPaint

由架構呼叫以處理 WM_PAINT 要求。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
容器所使用之裝置內容的指標。

### <a name="return-value"></a>傳回值

如果已處理訊息, 則為非零。否則為零。

### <a name="remarks"></a>備註

覆寫此函式以自訂繪製進程。

##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate

由架構在*pSite*所指向的控制網站即將就地啟用時所呼叫。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
要就地啟用之控制項網站的指標。

### <a name="remarks"></a>備註

就地啟用表示容器的主功能表會取代為就地複合功能表。

##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

當控制項網站 (由*pSite*指向) 即將停用時, 由架構呼叫。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
要停用之控制項網站的指標。

### <a name="remarks"></a>備註

收到此通知時, 容器應重新安裝其使用者介面並取得焦點。

##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren

由架構在從子視窗接收捲軸訊息時呼叫。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>參數

*dx*<br/>
沿著 X 軸的滾動量 (以圖元為單位)。

*dy*<br/>
沿著 y 軸的滾動量 (以圖元為單位)。

##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

將訊息傳送至指定的控制項。

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*nID*<br/>
指定接收訊息之控制項的識別碼。

*message*<br/>
指定要傳送的訊息。

*wParam*<br/>
指定其他訊息特定資訊。

*lParam*<br/>
指定其他訊息特定資訊。

##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

將對話方塊中控制項的文字設定為指定整數值的字串表示。

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別碼。

*nValue*<br/>
要顯示的整數值。

*bSigned*<br/>
指定*n 值*參數是帶正負號或不帶正負號。 如果此參數為 TRUE, 則*n 值*會經過簽署。 如果此參數為 TRUE 且*n 值*小於零, 則會在字串中的第一個數位前面放置一個減號。 如果此參數為 FALSE, 則表示*n 值*不帶正負號。

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

使用*lpszString*中包含的文字, 設定指定之控制項的文字。

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別碼。

*lpszString*<br/>
控制項文字的指標。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager 類別](../../mfc/reference/coccmanager-class.md)
