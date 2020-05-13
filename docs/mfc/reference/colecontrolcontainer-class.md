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
ms.openlocfilehash: 83171e012db7ef2cce459d35cfc689746afd062c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749022"
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
|[COle 控制容器:COle 控制容器](#colecontrolcontainer)|建構 `COleControlContainer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 控制容器::附加控制站台](#attachcontrolsite)|創建由容器託管的控制網站。|
|[COle 控制容器::廣播環境屬性更改](#broadcastambientpropertychange)|通知所有託管控件環境屬性已更改。|
|[COle 控制容器::檢查DlgButton](#checkdlgbutton)|修改指定的按鈕控制件。|
|[COle 控制容器::檢查無線按鈕](#checkradiobutton)|選擇組的指定單選按鈕。|
|[COle 控制容器:建立控制](#createcontrol)|創建託管的 ActiveX 控制件。|
|[COle 控制容器::建立 OleFont](#createolefont)|創建 OLE 字型。|
|[COle 控制容器:尋找專案](#finditem)|返回指定控制項的自訂網站。|
|[COle 控制容器::凍結所有事件](#freezeallevents)|確定控制網站是否接受事件。|
|[COle 控制容器:抓取環境](#getambientprop)|檢索指定的環境屬性。|
|[COle 控制容器::GetDlgItem](#getdlgitem)|檢索指定的對話方塊控制項。|
|[COle 控制容器::getDlgItemint](#getdlgitemint)|檢索指定的對話方塊控制項的值。|
|[COle 控制容器::取得DlgItemtext](#getdlgitemtext)|檢索指定對話方塊控制項的標題。|
|[COle 控制容器::手柄集焦點](#handlesetfocus)|確定容器是否處理WM_SETFOCUS消息。|
|[COle 控制容器::無視窗處理訊息](#handlewindowlessmessage)|處理發送到無視窗控制件的消息。|
|[COle 控制容器:IsDlgButton 檢查](#isdlgbuttonchecked)|確定指定按鈕的狀態。|
|[COle 控制容器::上漆](#onpaint)|調用以重新繪製容器的一部分。|
|[COle 控制容器::啟用 UI](#onuiactivate)|當控件即將就地啟動時調用。|
|[COle 控制容器:開啟](#onuideactivate)|當控件即將停用時調用。|
|[COle 控制容器::滾動子級](#scrollchildren)|當從子視窗接收滾動消息時,由框架調用。|
|[COle 控制容器::發送DlgItem消息](#senddlgitemmessage)|將訊息傳送至指定的控制項。|
|[COle 控制容器::SetDlgItemint](#setdlgitemint)|設置指定控制項的值。|
|[COle 控制容器::設定DlgItemtext](#setdlgitemtext)|設定指定控制項的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle 控制容器::m_crBack](#m_crback)|容器的背景顏色。|
|[COle 控制容器::m_crFore](#m_crfore)|容器的前景顏色。|
|[COle 控制容器::m_listSitesOrWnds](#m_listsitesorwnds)|支援的控制站點的清單。|
|[COle 控制容器::m_nWindowlessControls](#m_nwindowlesscontrols)|託管無視窗控制項的數量。|
|[COle 控制容器::m_pOleFont](#m_polefont)|指向自訂控制件站點的 OLE 字型的指標。|
|[COle 控制容器::m_pSiteCapture](#m_psitecapture)|指向捕獲控制網站的指標。|
|[COle 控制容器::m_pSiteFocus](#m_psitefocus)|指向當前具有輸入焦點的控制項的指標。|
|[COle 控制容器::m_pSiteUIActive](#m_psiteuiactive)|指向當前就地啟動的控件的指標。|
|[COle 控制容器::m_pWnd](#m_pwnd)|指向實現控制件容器的視窗的指標。|
|[COle 控制容器::m_siteMap](#m_sitemap)|網站地圖。|

## <a name="remarks"></a>備註

這是通過向一個或多個 ActiveX 控制網站提供支援(由`COleControlSite`實現) 來實現的。 `COleControlContainer`完全實現[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe)和[IOleContainer 介面](/windows/win32/api/oleidl/nn-oleidl-iolecontainer),允許包含的 ActiveX 控制件滿足其作為就地專案的資格。

通常,此類與`COccManager`和`COleControlSite`實現自訂 ActiveX 控制項容器結合使用,並結合一個或多個 ActiveX 控制項的自訂網站。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>需求

**標題:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COle 控制容器::附加控制站台

由框架調用以創建和附加控制件網站。

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
`CWnd` 物件的指標。

*nIDC*<br/>
要附加的控制項的 ID。

### <a name="remarks"></a>備註

如果要自定義此過程,請重寫此函數。

> [!NOTE]
> 如果要以靜態方式連結到 MFC 庫,請使用此函數的第一種形式。 如果要動態連結到 MFC 庫,請使用第二個窗體。

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COle 控制容器::廣播環境屬性更改

通知所有託管控件環境屬性已更改。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要更改的環境屬性的調度 ID。

### <a name="remarks"></a>備註

當環境屬性更改值時,框架將調用此功能。 重寫此函數以自定義此行為。

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COle 控制容器::檢查DlgButton

修改按鈕的當前狀態。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
要修改的按鈕的 ID。

*N檢查*<br/>
指定按鈕的狀態。 可以是下列其中一項：

- BST_CHECKED 將按鈕狀態設置為已選中狀態。

- BST_INDETERMINATE 將按鈕狀態設為灰色,指示不確定狀態。 僅當按鈕具有BS_3STATE或BS_AUTO3STATE樣式時,才使用此值。

- BST_UNCHECKED將按鈕狀態設置清除。

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COle 控制容器::檢查無線按鈕

在組中選擇指定的單選按鈕,並清除組中的剩餘按鈕。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>參數

*nID 第一按鈕*<br/>
指定群組中第一個單選按鈕的標識碼。

*nIDLastButton*<br/>
指定群組中最後一個單選按鈕的標識碼。

*NID 檢查按鈕*<br/>
指定要檢查的單選按鈕的標識碼。

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COle 控制容器:COle 控制容器

建構 `COleControlContainer` 物件。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向控制容器的父視窗的指標。

### <a name="remarks"></a>備註

成功建立物件後,添加一個自訂控制件站點,該站台將呼叫`AttachControlSite`。

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COle 控制容器:建立控制

建立由指定`COleControlSite`物件託管的 ActiveX 控制件。

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
指向表示控制項的視窗物件的指標。

*Clsid*<br/>
控制項的唯一類別 ID。

*lpsz 視窗名稱*<br/>
指向要在控制項中顯示的文本的指標。 設置控制項的標題或文字屬性的值(如果有)。 如果為 NULL,則控制的標題或文本屬性不會更改。

*dwStyle*<br/>
視窗樣式。 可用樣式列在 **「備註」** 部分下。

*矩形*<br/>
指定控制項的大小和位置。 它可以是`CRect`對`RECT`象或結構。

*nID*<br/>
指定控制項的子視窗 ID。

*p 堅持*<br/>
指向`CFile`包含控制的持久狀態的指標。 默認值為 NULL,指示控制項在不從任何持久儲存還原其狀態的情況下初始化自身。 如果不是 NULL,它應該是指向包含控制項持久資料`CFile`的 派生物件的指標,其形式是流或存儲。 此數據可能已保存在用戶端的上次啟動中。 `CFile`可以包含其他數據,但必須將其讀寫指標設置為調用`CreateControl`時持久性數據的第一個字節。

*b 儲存*<br/>
指示是否應將*pPersist*中的數據`IStorage`解釋`IStream`為 或數據。 如果*pPersist*中的數據是儲存,*則 b 儲存*應為 TRUE。 如果*pPersist*中的數據是流,*則 b 儲存*應為 FALSE。 預設值為 FALSE。

*bstrLicKey*<br/>
可選的許可證金鑰資料。 僅創建需要運行時許可證密鑰的控制項才需要此資料。 如果控制項支援許可,則必須提供許可證金鑰才能成功建立控制項。 預設值是 NULL。

*ppNewSite*<br/>
指向將承載正在創建的控制件的現有控制站點的指標。 預設值為 NULL,表示將自動建立新的控制項網站並附加到新控制項。

*Ppt*<br/>
指向包含控制項左`POINT`上角的結構的指標。 控制項大小由*size*的值決定。 *ppt*和*size 值*是指定控制項大小和位置的可選方法。

*psize*<br/>
指向包含控制大小的`SIZE`結構的指標。 左上角由*ppt*的值決定。 *ppt*和*size 值*是指定控制項大小和位置的可選方法。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

只有 Windows *dwStyle*標誌的`CreateControl`子集受 支援:

- WS_VISIBLE 創建最初可見的視窗。 如果希望控件立即可見(如普通視窗),則需要。

- WS_DISABLED 創建最初禁用的視窗。 禁用的視窗無法接收使用者輸入。 如果控件具有"已啟用"屬性,則可以進行設置。

- WS_BORDER 創建具有細線邊框的視窗。 如果控件具有 BorderStyle 屬性,則可以進行設置。

- WS_GROUP 指定一組控制件的第一個控制項。 用戶可以使用方向鍵將鍵盤焦點從組中的一個控制項更改為下一個控制項。 在第一個控制項之後使用WS_GROUP樣式定義的所有控制項都屬於同一組。 具有WS_GROUP樣式的下一個控制項將結束組並啟動下一個組。

- WS_TABSTOP 指定可在使用者按下 TAB 鍵時接收鍵盤焦點的控制項。 按下 TAB 鍵會將鍵盤焦點更改為WS_TABSTOP樣式的下一個控制項。

使用第二個重載創建預設大小的控制項。

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COle 控制容器::建立 OleFont

創建 OLE 字型。

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
指向控制容器使用的字型的指標。

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COle 控制容器:尋找專案

查找承載指定項的自定義網站。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
要找到的項的標識符。

### <a name="return-value"></a>傳回值

指向指定項的自定義網站的指標。

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COle 控制容器::凍結所有事件

確定容器是忽略來自附加控制網站的事件還是接受這些事件。

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>參數

*bFreeze*<br/>
如果將處理事件,則非零;否則 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果控制容器請求,則不需要該控件停止觸發事件。 它可以繼續觸發,但控制容器將忽略所有後續事件。

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COle 控制容器:抓取環境

檢索指定環境屬性的值。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>參數

*pSite*<br/>
指向將從中檢索環境屬性的控制網站的指標。

*不一部分*<br/>
所需環境屬性的調度 ID。

*pVarResult*<br/>
指向環境屬性值的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COle 控制容器::GetDlgItem

在對話框或其他視窗中檢索指向指定控制項或子視窗的指標。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
要檢索的對話方塊項的標識符。

*phwnd*<br/>
指向指定對話框項視窗物件的句柄的指標。

### <a name="return-value"></a>傳回值

指向對話框項視窗的指標。

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COle 控制容器::getDlgItemint

檢索給定控件的翻譯文本的值。

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控件的標識碼。

*lpTrans*<br/>
指向接收函數成功/失敗值的布爾變數的指標(TRUE表示成功,FALSE 表示失敗)。

*b簽章*<br/>
指定函數是否應在開頭檢查文本中的減號,並在找到已簽名的整數值時返回該值。 如果*bSigned 參數*為 TRUE,則指定要檢索的值是已簽名的整數值,則將返回值轉換為**int**類型。 要取得延伸的錯誤資訊,請致電[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="return-value"></a>傳回值

如果成功 *,lpTrans*指向的變數將設置為 TRUE,返回值是控制項文本的已轉換值。

如果函數失敗 *,lpTrans*指向的變數將設置為 FALSE,返回值為零。 請注意,由於零是可能翻譯的值,因此返回值為零本身並不表示失敗。

如果*lpTrans*為 NULL,則函數不會返回任何有關成功或失敗的資訊。

### <a name="remarks"></a>備註

該函數通過剝離文本開頭的任何額外空格,然後轉換十進位數字來轉換檢索的文本。 當函數到達文本末尾或遇到非數位字元時,該函數將停止翻譯。

如果轉換的值大於INT_MAX(對於簽名數位)或UINT_MAX(對於未簽名的數位),則此功能返回零。

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COle 控制容器::取得DlgItemtext

檢索給定控件的文本。

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控件的標識碼。

*lpStr*<br/>
指向控制項文字的指標。

*nMax( N) Count*<br/>
指定要複製到*lpStr*指向的緩衝區的字串的最大長度(以字元表示) 如果字串的長度超過限制,則該字串將被截斷。

### <a name="return-value"></a>傳回值

如果函數成功,返回值將指定複製到緩衝區的字元數,不包括終止空字元。

如果此函式失敗，則傳回值為零。 要取得延伸的錯誤資訊,請致電[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COle 控制容器::手柄集焦點

確定容器是否處理WM_SETFOCUS消息。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>傳回值

如果容器處理WM_SETFOCUS消息,則非零;否則為零。

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COle 控制容器::無視窗處理訊息

處理無視窗控制件的視窗訊息。

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>參數

*message*<br/>
視窗消息的標識碼,由 Windows 提供。

*wParam*<br/>
消息的參數;由 Windows 提供。 指定其他特定於消息的資訊。 此參數的內容取決於*消息*參數的值。

*lParam*<br/>
消息的參數;由 Windows 提供。 指定其他特定於消息的資訊。 此參數的內容取決於*消息*參數的值。

*PlResult*<br/>
視窗結果代碼。 指定消息處理的結果,並取決於發送的消息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

重寫此函數以自定義無視窗控制消息的處理。

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COle 控制容器:IsDlgButton 檢查

確定指定按鈕的狀態。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

返回值,來自使用BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON 或BS_3STATE樣式創建的按鈕。 可以是下列其中一項：

- BST_CHECKED按鈕選中。

- BST_INDETERMINATE按鈕為灰色,指示不確定狀態(僅適用於按鈕具有BS_3STATE或BS_AUTO3STATE樣式時)。

- BST_UNCHECKED按鈕清除。

### <a name="remarks"></a>備註

如果按鈕是三狀態控件,則成員函數將確定該按鈕是變暗、選中還是兩者均未調暗。

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COle 控制容器::m_crBack

容器的背景顏色。

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COle 控制容器::m_crFore

容器的前景顏色。

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COle 控制容器::m_listSitesOrWnds

容器託管的控制站台的清單。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COle 控制容器::m_nWindowlessControls

控制容器託管的無視窗控制項。

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COle 控制容器::m_pOleFont

指向自訂控制件站點的 OLE 字型的指標。

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COle 控制容器::m_pSiteCapture

指向捕獲控制網站的指標。

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COle 控制容器::m_pSiteFocus

指向當前具有輸入焦點的控制網站的指標。

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COle 控制容器::m_pSiteUIActive

指向就地啟動的控制網站的指標。

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COle 控制容器::m_pWnd

指向與容器關聯的視窗物件的指標。

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COle 控制容器::m_siteMap

網站地圖。

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COle 控制容器::上漆

由框架調用以處理WM_PAINT請求。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向容器使用的設備上下文的指標。

### <a name="return-value"></a>傳回值

處理消息時非零;否則為零。

### <a name="remarks"></a>備註

重寫此函數以自定義繪製過程。

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COle 控制容器::啟用 UI

當控制網站(由*pSite*指向)即將就地啟動時,由框架調用。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
指向即將就地啟動的控制網站的指標。

### <a name="remarks"></a>備註

就地激活意味著容器的主菜單替換為就地複合功能表。

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COle 控制容器:開啟

當控制站台(*由 pSite*指向)即將停用時,由框架調用。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
指向即將停用的控制網站的指標。

### <a name="remarks"></a>備註

收到此通知時,容器應重新安裝其使用者介面並集中注意力。

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COle 控制容器::滾動子級

當從子視窗接收滾動消息時,由框架調用。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>參數

*Dx*<br/>
沿 x 軸滾動的數量(以像素為單位)。

*Dy*<br/>
沿 y 軸滾動的數量(以像素為單位)。

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COle 控制容器::發送DlgItem消息

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
指定接收訊息的控制項的識別碼。

*message*<br/>
指定要發送的消息。

*wParam*<br/>
指定其他特定於消息的資訊。

*lParam*<br/>
指定其他特定於消息的資訊。

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COle 控制容器::SetDlgItemint

將對話框中控制件的文本設定為指定整數值的字串表示形式。

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>參數

*nID*<br/>
控件的標識碼。

*n值*<br/>
要顯示的整數值。

*b簽章*<br/>
指定*nValue*參數是簽名還是未簽署。 如果此參數為 TRUE,則*對 nValue*進行簽名。 如果此參數為*TRUE,nValue*小於零,則在字串中的第一個數位之前放置一個減號。 如果此參數為 FALSE,*則 nValue*是無符號的。

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COle 控制容器::設定DlgItemtext

使用*lpszString*中包含的文字設定指定控制項的文字。

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nID*<br/>
控件的標識碼。

*lpszString*<br/>
指向控制項文字的指標。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COle 控制網站類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager 類別](../../mfc/reference/coccmanager-class.md)
