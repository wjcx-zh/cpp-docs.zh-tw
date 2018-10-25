---
title: COleControlContainer 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd45453dd4d70424b47f74e46d0bd5f948f75499
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077695"
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

|名稱|描述|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|建立控制項的站台，由容器所裝載。|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|會通知所有裝載環境的屬性已變更的控制項。|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按鈕控制項。|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|選取指定的選項按鈕的群組。|
|[COleControlContainer::CreateControl](#createcontrol)|建立裝載的 ActiveX 控制項。|
|[COleControlContainer::CreateOleFont](#createolefont)|建立 OLE 字型。|
|[COleControlContainer::FindItem](#finditem)|傳回指定之控制項的自訂站台。|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|決定控制項站台接受事件。|
|[COleControlContainer::GetAmbientProp](#getambientprop)|擷取指定的環境屬性。|
|[COleControlContainer::GetDlgItem](#getdlgitem)|擷取指定的對話方塊控制項。|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|擷取指定的對話方塊控制項的值。|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|擷取指定的對話方塊控制項的標題。|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|決定是否容器在處理 WM_SETFOCUS 訊息。|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|處理傳送至無視窗控制項的訊息。|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|判斷指定的按鍵的狀態。|
|[COleControlContainer::OnPaint](#onpaint)|呼叫以重新繪製容器的一部分。|
|[COleControlContainer::OnUIActivate](#onuiactivate)|就地啟動控制項時呼叫。|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|停用控制項時呼叫。|
|[COleControlContainer::ScrollChildren](#scrollchildren)|從子視窗接收捲動訊息時由架構呼叫。|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|將訊息傳送至指定的控制項。|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|設定指定控制項的值。|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|設定指定控制項的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|容器的背景色彩。|
|[COleControlContainer::m_crFore](#m_crfore)|容器的前景色彩。|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|支援的控制項站台的清單。|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|裝載的無視窗控制項數目。|
|[COleControlContainer::m_pOleFont](#m_polefont)|OLE 字型自訂控制項站台的指標。|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|擷取控制項站台的指標。|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|目前擁有輸入焦點之控制項的指標。|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|目前為就地啟動之控制項的指標。|
|[COleControlContainer::m_pWnd](#m_pwnd)|實作控制項容器的視窗指標。|
|[COleControlContainer::m_siteMap](#m_sitemap)|站台對應。|

## <a name="remarks"></a>備註

這是藉由提供對一或多個 ActiveX 控制項站台的支援 (藉由將`COleControlSite`)。 `COleControlContainer` 完整實作[IOleInPlaceFrame](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceframe)並[IOleContainer](/windows/desktop/api/oleidl/nn-oleidl-iolecontainer)介面，讓包含的 ActiveX 控制項，以滿足其資格做為就地項目。

通常，這個類別用於搭配`COccManager`和`COleControlSite`來實作自訂的 ActiveX 控制項容器，使用一或多個 ActiveX 控制項的自訂網站。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>需求

**標頭：** afxocc.h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

由架構呼叫以建立並附加控制項站台。

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
要附加的控制項 ID。

### <a name="remarks"></a>備註

如果您想要自訂此程序，請覆寫這個函式。

> [!NOTE]
>  如果您要以靜態方式連結 MFC 程式庫，請使用此函式的第一個表單。 如果您要以動態方式連結 MFC 程式庫，請使用第二種形式。

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

會通知所有裝載環境的屬性已變更的控制項。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
正在變更的環境屬性的分派識別碼。

### <a name="remarks"></a>備註

環境屬性已變更值時，此函式是由架構呼叫。 此函式以自訂此行為來覆寫。

##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton

修改按鈕的目前狀態。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
修改按鈕的識別碼。

*n*<br/>
指定按鈕的狀態。 可以是下列其中一項：

- BST_CHECKED 集按鈕的狀態，若要檢查。

- BST_INDETERMINATE 設定按鈕狀態顯示為灰色，表示為未決狀態。 只有當按鈕的 BS_3STATE 或 BS_AUTO3STATE 樣式，請使用此值。

- BST_UNCHECKED 集清除的按鈕狀態。

##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton

選取指定的選項按鈕群組中，並清除群組中其餘的按鈕。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>參數

*nIDFirstButton*<br/>
指定群組中的第一個選項按鈕的識別碼。

*nIDLastButton*<br/>
指定群組中的最後一個選項按鈕的識別碼。

*nIDCheckButton*<br/>
指定要檢查的選項按鈕的識別碼。

##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer

建構 `COleControlContainer` 物件。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
控制項容器的父視窗指標。

### <a name="remarks"></a>備註

物件已成功建立之後，新增自訂控制項網站呼叫`AttachControlSite`。

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

建立 ActiveX 控制項，由指定裝載`COleControlSite`物件。

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
表示控制項的視窗物件的指標。

*clsid*<br/>
控制項的唯一類別 ID。

*lpszWindowName*<br/>
要在控制項中顯示的文字指標。 （如果有的話），請設定控制項的標題或文字屬性的值。 如果是 NULL，不會變更控制項的標題或文字屬性。

*cheaderctrl:: Create*<br/>
視窗樣式。 底下會列出可用的樣式**備註**一節。

*rect*<br/>
指定控制項的大小和位置。 它可以是`CRect`物件或`RECT`結構。

*nID*<br/>
指定控制項的子視窗識別碼。

*pPersist*<br/>
指標`CFile`包含控制項的永續性狀態。 預設值是 NULL，表示控制項，而不還原其狀態從任何持續性儲存體初始化本身。 如果不是 NULL，它應該是一個指向`CFile`-衍生物件，包含控制項的永續性資料，資料流或儲存體的形式。 這項資料可以儲存在用戶端上啟用。 `CFile`可以包含其他資料，但必須設定為永續性資料的第一個位元組時呼叫它讀寫指標`CreateControl`。

*bStorage*<br/>
指出是否在資料*pPersist*應解譯為`IStorage`或`IStream`資料。 如果中的資料*pPersist*是儲存體*bStorage*應該是 TRUE。 如果中的資料*pPersist*是資料流*bStorage*應該是 FALSE。 預設值為 FALSE。

*bstrLicKey*<br/>
選擇性的授權金鑰資料。 這項資料只能在建立需要的執行階段授權金鑰的控制項。 如果此控制項支援授權，您必須提供授權金鑰建立的控制項才會成功。 預設值是 NULL。

*ppNewSite*<br/>
將要裝載控制項所建立的現有控制項站台指標。 預設值是 NULL，表示，新的控制項站台會自動建立並附加至新的控制項。

*ppt*<br/>
指標`POINT`結構，包含控制項的左上角。 控制項的大小取決於 windows 7 *psize*。 *Ppt*並*psize*值是選擇性的方法，來指定的大小和位置的控制項。

*psize*<br/>
指標`SIZE`結構，包含控制項的大小。 值來決定左上角*ppt*。 *Ppt*並*psize*值是選擇性的方法，來指定的大小和位置的控制項。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

只是 Windows 的子集*cheaderctrl:: Create*旗標受到`CreateControl`:

- WS_VISIBLE 會建立一開始即可見的視窗。 如果您想看見立即，像一般的 windows 控制項的必要項。

- WS_DISABLED 會建立一開始會停用的視窗。 停用的視窗無法接收來自使用者的輸入。 如果控制項具有已啟用屬性，可以設定。

- WS_BORDER 會建立具有精簡列框線的視窗。 如果控制項的框線樣式屬性，可以設定。

- WS_GROUP 指定控制項群組的第一個控制項。 使用者可以變更鍵盤焦點從群組中的一個控制項到下一個使用方向鍵。 之後的第一個控制項屬於相同的群組，以 WS_GROUP 樣式定義的所有控制項。 WS_GROUP 樣式的下一個控制項結束該群組，並開始下一步 群組。

- WS_TABSTOP 指定當使用者按下 TAB 鍵時，可以接收鍵盤焦點的控制項。 按下 TAB 鍵若 WS_TABSTOP 樣式的下一個控制項来變更鍵盤焦點。

您可以使用第二個多載來建立預設大小的控制項。

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

建立 OLE 字型。

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
指標，以供控制項容器的字型。

##  <a name="finditem"></a>  COleControlContainer::FindItem

尋找自訂站台裝載指定的項目。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
要找的項目識別項。

### <a name="return-value"></a>傳回值

自訂的網站所指定項目的指標。

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

決定容器將會忽略事件，從連接的控制站台或接受這些條款。

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>參數

*bFreeze*<br/>
將處理的事件; 如果為非零否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  不需要停止引發事件，如果控制項容器所要求的控制項。 它可以繼續引發，但控制項容器會略過所有後續的事件。

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

擷取指定的環境屬性的值。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>參數

*pSite*<br/>
控制站台環境的屬性會擷取的指標。

*dispid*<br/>
所需的環境屬性的分派識別碼。

*pVarResult*<br/>
環境屬性的值的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

擷取在對話方塊中指定的控制項或子視窗或其他視窗的指標。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
若要擷取之對話方塊項目的識別碼。

*phWnd*<br/>
指定的對話方塊項目的視窗物件的控制代碼指標。

### <a name="return-value"></a>傳回值

對話方塊項目的視窗的指標。

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

擷取指定控制項的翻譯的文字值。

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別項。

*lpTrans*<br/>
接收函式成功/失敗值的布林值變數的指標 （TRUE 表示成功，FALSE 表示失敗）。

*bSigned*<br/>
指定函式是否應該檢查負號開頭的文字，並傳回帶正負號的整數值，如果找到。 如果*bSigned*參數為 TRUE，則指定要擷取的值帶正負號的整數值，傳回值轉換成**int**型別。 若要取得延伸錯誤資訊，請呼叫[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

### <a name="return-value"></a>傳回值

如果成功，變數所指向*lpTrans*設為 TRUE，且傳回的值為控制項文字的已翻譯的值。

如果函式失敗，變數所指向*lpTrans*設為 FALSE，則傳回值為零。 請注意，由於零是可能的已翻譯的值，傳回的值為零不會單獨使用時指出失敗。

如果*lpTrans*是 NULL，函式會傳回任何資訊成功或失敗。

### <a name="remarks"></a>備註

此函式以移除任何多餘的空格開頭的文字，然後將轉換的十進位數字轉換擷取的文字。 函式中，就會停止轉譯當它到達文字末端，或遇到非數字的字元。

已翻譯的值是否大於 INT_MAX （適用於帶正負號的數字） 或 UINT_MAX （適用於不帶正負號的數字），此函式會傳回零。

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

擷取指定控制項的文字。

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別項。

*lpStr*<br/>
控制項的文字指標。

*nMaxCount*<br/>
指定的最大長度，以字元為單位複製到所指向緩衝區的字串*lpStr*。 如果字串的長度超過限制時，會截斷字串。

### <a name="return-value"></a>傳回值

如果此函數成功，傳回的值會指定複製到緩衝區，不包括結束的 null 字元的字元數。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

決定是否容器在處理 WM_SETFOCUS 訊息。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>傳回值

非零值，如果容器會處理 WM_SETFOCUS 訊息;否則為零。

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

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
視窗訊息，Windows 所提供的識別項。

*wParam*<br/>
訊息; 參數由 Windows 所提供。 指定特定訊息的其他資訊。 此參數的內容而定的值*訊息*參數。

*lParam*<br/>
訊息; 參數由 Windows 所提供。 指定特定訊息的其他資訊。 此參數的內容而定的值*訊息*參數。

*plResult*<br/>
Windows 結果碼。 指定訊息處理的結果，取決於傳送的訊息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

覆寫此函式可自訂的無視窗的控制訊息處理。

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

判斷指定的按鍵的狀態。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>參數

*nIDButton*<br/>
按鈕控制項的識別項。

### <a name="return-value"></a>傳回值

傳回值，由以 BS_AUTOCHECKBOX、 BS_AUTORADIOBUTTON、 BS_AUTO3STATE、 BS_CHECKBOX、 BS_RADIOBUTTON，還是 BS_3STATE 樣式的按鈕。 可以是下列其中一項：

- 核取 BST_CHECKED 按鈕。

- BST_INDETERMINATE 按鈕會變為灰色，表示不定狀態 （僅適用於按鈕具有 BS_3STATE 或 BS_AUTO3STATE 樣式時）。

- 會清除 BST_UNCHECKED 按鈕。

### <a name="remarks"></a>備註

如果按鈕是三種狀態控制項，此成員函式會決定是否就會呈暗灰色，核取，或兩者都關閉。

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

容器的背景色彩。

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

容器的前景色彩。

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

容器所裝載的控制項站台的清單。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

無視窗控制項容器所裝載的控制項數目。

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

OLE 字型自訂控制項站台的指標。

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

擷取控制項站台的指標。

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

控制項站台目前擁有輸入焦點指標。

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

控制項站台就地啟用的指標。

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

與容器相關聯的視窗物件的指標。

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

站台對應。

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>  COleControlContainer::OnPaint

由架構呼叫以處理 WM_PAINT 要求。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
容器所使用的裝置內容指標。

### <a name="return-value"></a>傳回值

非零值，如果已處理的訊息;否則為零。

### <a name="remarks"></a>備註

覆寫此函式可自訂的繪製程序。

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

由架構呼叫，當控制項站台，指向*pSite*，即將就地啟動。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
控制項站台，即將就地啟動指標。

### <a name="remarks"></a>備註

在就地啟用表示容器的主功能表會取代就地組合功能表。

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

由架構呼叫，當控制項站台，指向*pSite*，即將予以停用。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>參數

*pSite*<br/>
控制項站台，即將予以停用指標。

### <a name="remarks"></a>備註

收到此通知時，容器應重新安裝它的使用者介面，並取得焦點。

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

從子視窗接收捲動訊息時由架構呼叫。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>參數

*dx*<br/>
沿著 x 軸的捲動的量，單位為像素。

*dy*<br/>
沿 y 軸的捲動的量，單位為像素。

##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage

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
指定接收訊息的控制項識別碼。

*message*<br/>
指定要傳送的訊息。

*wParam*<br/>
指定特定訊息的其他資訊。

*lParam*<br/>
指定特定訊息的其他資訊。

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

在對話方塊中指定的整數值的字串表示来設定控制項的文字。

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別項。

*n 值*<br/>
要顯示的整數值。

*bSigned*<br/>
指定是否*n 值*參數為帶正負號或不帶正負號。 如果此參數為 TRUE， *n 值*簽署。 如果此參數為 TRUE 並*n 值*小於零，正負號放在字串中的第一個數字前面的減號。 如果此參數為 FALSE 時， *n 值*不帶正負號。

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

設定指定的控制項，並使用文字中包含的文字*lpszString*。

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nID*<br/>
控制項的識別項。

*lpszString*<br/>
控制項的文字指標。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager 類別](../../mfc/reference/coccmanager-class.md)
