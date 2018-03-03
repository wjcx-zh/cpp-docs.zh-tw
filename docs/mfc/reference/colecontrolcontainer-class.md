---
title: "COleControlContainer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6d04faa904eba416b290515e5e6773ac6ef9837
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|建立控制項的站台，容器所裝載。|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|通知所有託管環境的屬性已變更的控制項。|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按鈕控制項。|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|選取一組指定的選項的按鈕。|  
|[COleControlContainer::CreateControl](#createcontrol)|建立裝載的 ActiveX 控制項。|  
|[COleControlContainer::CreateOleFont](#createolefont)|建立 OLE 字型。|  
|[COleControlContainer::FindItem](#finditem)|傳回指定之控制項的自訂站台。|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|決定是否控制項站台接受事件。|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|擷取指定的環境屬性。|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|擷取指定的對話方塊控制項。|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|擷取指定的對話方塊控制項的值。|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|擷取指定的對話方塊控制項的標題。|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|決定是否容器處理`WM_SETFOCUS`訊息。|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|會處理訊息傳送至無視窗控制項。|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|判斷指定的按鍵的狀態。|  
|[COleControlContainer::OnPaint](#onpaint)|呼叫以重新繪製容器之一部分。|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|就地啟動控制項時呼叫。|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|當控制項被停用時呼叫。|  
|[COleControlContainer::ScrollChildren](#scrollchildren)|從子視窗接收捲動訊息時由架構呼叫。|  
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|將訊息傳送至指定的控制項。|  
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|設定指定之控制項的值。|  
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|設定指定之控制項的文字。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControlContainer::m_crBack](#m_crback)|容器的背景色彩。|  
|[COleControlContainer::m_crFore](#m_crfore)|容器的前景色彩。|  
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|支援的控制項站台的清單。|  
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|託管的無視窗控制項數目。|  
|[COleControlContainer::m_pOleFont](#m_polefont)|自訂控制項站台的 OLE 字型指標。|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|擷取控制項站台的指標。|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|目前擁有輸入焦點之控制項的指標。|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|目前在就地啟用的控制項的指標。|  
|[COleControlContainer::m_pWnd](#m_pwnd)|實作控制項容器視窗的指標。|  
|[COleControlContainer::m_siteMap](#m_sitemap)|站台對應。|  
  
## <a name="remarks"></a>備註  
 這是由提供一個或多個 ActiveX 控制項網站的支援 (藉由`COleControlSite`)。 `COleControlContainer`全面實作[IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770)和[IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103)介面，讓所包含的 ActiveX 控制項，以滿足其條件為就地項目。  
  
 通常，這個類別用來搭配`COccManager`和`COleControlSite`來實作自訂的 ActiveX 控制項容器，與一或多個 ActiveX 控制項的自訂網站。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxocc.h  
  
##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite  
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
 `pWnd`  
 指標`CWnd`物件。  
  
 `nIDC`  
 要附加的控制項識別碼。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂這個程序，覆寫這個函式。  
  
> [!NOTE]
>  如果您要以靜態方式連結 MFC 程式庫，請使用此函式的第一個表單。 如果您要以動態方式連結 MFC 程式庫，請使用第二種形式。  
  
##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange  
 通知所有託管環境的屬性已變更的控制項。  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要變更的環境屬性的分派 ID。  
  
### <a name="remarks"></a>備註  
 當環境的屬性值變更時，此函式是由架構呼叫。 此函式以自訂此行為來覆寫。  
  
##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton  
 修改按鍵的目前狀態。  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>參數  
 `nIDButton`  
 要修改的按鈕的識別碼。  
  
 `nCheck`  
 指定按鈕的狀態。 可以是下列其中一項：  
  
- **BST_CHECKED**按鈕狀態設定為已核取。  
  
- **BST_INDETERMINATE**按鈕狀態設定為灰色，表示為未決狀態。 使用此值，只有當按鈕的**BS_3STATE**或**BS_AUTO3STATE**樣式。  
  
- **BST_UNCHECKED**按鈕狀態設定為已清除。  
  
##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton  
 選取指定的選項按鈕群組中，並清除群組中其餘的按鈕。  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>參數  
 `nIDFirstButton`  
 指定的識別項的第一個選項按鈕群組中。  
  
 `nIDLastButton`  
 指定群組中的最後一個選項按鈕的識別項。  
  
 `nIDCheckButton`  
 指定要檢查的選項按鈕的識別項。  
  
##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer  
 建構 `COleControlContainer` 物件。  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 控制項容器的父視窗指標。  
  
### <a name="remarks"></a>備註  
 一旦物件建立成功，將自訂控制項的站台的呼叫`AttachControlSite`。  
  
##  <a name="createcontrol"></a>COleControlContainer::CreateControl  
 建立 ActiveX 控制項，指定裝載`COleControlSite`物件。  
  
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
 `pWndCtrl`  
 表示控制項的視窗物件的指標。  
  
 `clsid`  
 控制項的唯一類別 ID。  
  
 `lpszWindowName`  
 要在控制項中顯示的文字指標。 （如果有的話），請設定控制項的標題或文字屬性的值。 如果**NULL**，則不會變更控制項的標題或文字屬性。  
  
 `dwStyle`  
 視窗樣式。 可用的樣式會列在下**備註**> 一節。  
  
 `rect`  
 指定控制項的大小和位置。 它可以是`CRect`物件或`RECT`結構。  
  
 `nID`  
 指定控制項的子視窗識別碼。  
  
 `pPersist`  
 指標`CFile`包含控制項的永續性狀態。 預設值是**NULL**，指出此控制項，而不還原其狀態從任何永續性儲存體初始化本身。 如果沒有**NULL**，它應該指向的`CFile`-衍生物件，包含控制項的永續性資料，請在資料流或儲存體的格式。 這項資料可以儲存在用戶端上啟用。 `CFile`可以包含其他資料，但必須設定的持續性資料的第一個位元組時呼叫其讀寫指標`CreateControl`。  
  
 `bStorage`  
 指出是否在資料`pPersist`應該解譯為`IStorage`或`IStream`資料。 如果中的資料`pPersist`是儲存體，`bStorage`應該**TRUE**。 如果在資料`pPersist`是 stream，`bStorage`應該**FALSE**。 預設值是**FALSE**。  
  
 `bstrLicKey`  
 選擇性的授權金鑰資料。 此資料只需要建立需要的執行階段授權識別碼的控制項。 如果此控制項支援授權，您必須提供控制項才會成功建立授權金鑰。 預設值是**NULL**。  
  
 *ppNewSite*  
 現有的控制項站台會裝載在建立控制項的指標。 預設值是**NULL**，指出，新的控制項站台時會自動建立及附加到新的控制項。  
  
 `ppt`  
 指標**點**結構，包含控制項的左上角。 控制項的大小取決於值*psize*。 `ppt`和*psize*值是選擇性的方法，可指定的大小和位置的控制項。  
  
 *psize*  
 指標**大小**結構，包含控制項的大小。 左上角的值來決定`ppt`。 `ppt`和*psize*值是選擇性的方法，可指定的大小和位置的控制項。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 只有 Windows 子集`dwStyle`旗標受到`CreateControl`:  
  
- **WS_VISIBLE**建立一開始即可見的視窗。 如果您想看見立即像一般的 windows 控制項的必要項。  
  
- **WS_DISABLED**建立視窗一開始停用。 停用的視窗無法接收使用者輸入。 如果控制項具有已啟用屬性，可以設定。  
  
- `WS_BORDER`建立具有精簡列框線的視窗。 如果控制項的框線樣式屬性，可以設定。  
  
- **WS_GROUP**指定控制項群組的第一個控制項。 使用者可以變更鍵盤焦點從一個控制項群組中至下一個使用方向鍵。 所有控制項，以定義**WS_GROUP**樣式之後的第一個控制項必須屬於相同的群組。 下一個控制項與**WS_GROUP**樣式結束的群組，並啟動下一個群組。  
  
- **WS_TABSTOP**指定控制項可接收鍵盤焦點時使用者按下 TAB 鍵。 按下 TAB 鍵的鍵盤焦點變更到下一個控制項的**WS_TABSTOP**樣式。  
  
 您可以使用第二個多載來建立預設大小的控制項。  
  
##  <a name="createolefont"></a>COleControlContainer::CreateOleFont  
 建立 OLE 字型。  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 指標，用於透過控制項容器的字型。  
  
##  <a name="finditem"></a>COleControlContainer::FindItem  
 尋找裝載指定的項目自訂站台。  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 要尋找的項目識別項。  
  
### <a name="return-value"></a>傳回值  
 自訂的網站所指定項目的指標。  
  
##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents  
 請判斷容器將會忽略事件，從連接的控制站台或同意這些授權條款。  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>參數  
 `bFreeze`  
 為非零，如果事件處理。否則便是 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  不需要停止引發事件，如果控制項容器所要求的控制項。 它可以繼續引發，但控制項容器會略過所有後續的事件。  
  
##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp  
 擷取指定的環境屬性的值。  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>參數  
 `pSite`  
 指向控制項站台將會擷取環境的屬性。  
  
 `dispid`  
 所需的環境屬性的分派識別碼。  
  
 *pVarResult*  
 環境屬性的值的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem  
 擷取在對話方塊中指定的控制項或子視窗或其他視窗的指標。  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 擷取對話方塊項目的識別碼。  
  
 `phWnd`  
 指定的對話方塊項目的視窗物件的控制代碼指標。  
  
### <a name="return-value"></a>傳回值  
 對話方塊項目的視窗的指標。  
  
##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt  
 擷取值，指定控制項的已翻譯文字。  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制項的識別項。  
  
 `lpTrans`  
 接收函式成功/失敗值的布林變數的指標 ( **TRUE**表示成功， **FALSE**表示失敗)。  
  
 `bSigned`  
 指定函式是否應該檢查負號開頭的文字，並傳回帶正負號的整數值，如果找到。 如果`bSigned`參數是**TRUE**，指定要擷取的值帶正負號的整數值，將傳回值轉換為`int`型別。 若要取得延伸錯誤資訊，請呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，變數所指向`lpTrans`設**TRUE**，且傳回的值為控制項文字的已翻譯的值。  
  
 如果函式失敗，變數所指向`lpTrans`設**FALSE**，並傳回值為零。 請注意，由於零是可能的已翻譯的值，傳回值為零不本身會指出失敗。  
  
 如果`lpTrans`是**NULL**，此函數會傳回沒有成功或失敗的資訊。  
  
### <a name="remarks"></a>備註  
 此函式會將擷取的文字轉譯條狀配置任何額外的空格開頭的文字，然後將轉換的十進位數字。 函式會停止轉譯它到達文字末端，或在遇到非數字字元。  
  
 此函數會傳回零，如果轉譯後的值大於**INT_MAX** （為帶正負號數字） 或**UINT_MAX** （適用於不帶正負號的數字）。  
  
##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText  
 擷取指定的控制項的文字。  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制項的識別項。  
  
 `lpStr`  
 控制項的文字指標。  
  
 `nMaxCount`  
 指定以字元為單位，要複製到緩衝區所指向之字串的長度上限， `lpStr`。 如果字串的長度超過限制，系統會截斷字串。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回值會指定字元複製到緩衝區，不包括結束的 null 字元的數。  
  
 如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus  
 決定是否容器處理`WM_SETFOCUS`訊息。  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果容器處理`WM_SETFOCUS`訊息; 否則為零。  
  
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
 `message`  
 視窗訊息，Windows 所提供的識別項。  
  
 `wParam`  
 參數的訊息。由 Windows 所提供。 指定特定訊息的其他資訊。 此參數的內容而定的值`message`參數。  
  
 `lParam`  
 參數的訊息。由 Windows 所提供。 指定特定訊息的其他資訊。 此參數的內容而定的值`message`參數。  
  
 *plResult*  
 Windows 結果碼。 指定訊息處理的結果，取決於訊息傳送。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可自訂的無視窗控制項訊息處理。  
  
##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked  
 判斷指定的按鍵的狀態。  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIDButton`  
 按鈕控制項的識別項。  
  
### <a name="return-value"></a>傳回值  
 傳回值，從按鈕，以建立**BS_AUTOCHECKBOX**， **BS_AUTORADIOBUTTON**， **BS_AUTO3STATE**， **BS_CHECKBOX**，**BS_RADIOBUTTON**，或**BS_3STATE**樣式。 可以是下列其中一項：  
  
- **BST_CHECKED**核取按鈕。  
  
- **BST_INDETERMINATE**按鈕會變成灰色，表示不確定的狀態 (僅適用於該按鈕**BS_3STATE**或**BS_AUTO3STATE**樣式)。  
  
- **BST_UNCHECKED**按鈕會被清除。  
  
### <a name="remarks"></a>備註  
 如果按鈕是三種狀態控制項，此成員函式判斷是否就會呈暗灰色，選取此選項，或兩者都關閉。  
  
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
 容器所裝載的控制項站台的清單。  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls  
 無視窗控制項容器所裝載的控制項數目。  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont  
 自訂控制項站台的 OLE 字型指標。  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture  
 擷取控制項站台的指標。  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus  
 指向的目前擁有輸入焦點的控制項站台。  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive  
 控制項站台就地啟動的指標。  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd  
 與容器相關聯的視窗物件的指標。  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap  
 站台對應。  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="onpaint"></a>COleControlContainer::OnPaint  
 由架構呼叫以處理`WM_PAINT`要求。  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 容器所使用的裝置內容的指標。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已處理訊息。否則為零。  
  
### <a name="remarks"></a>備註  
 此函式可自訂的繪製程序會覆寫。  
  
##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate  
 由架構呼叫時，控制站台所指`pSite`，即將就地啟動。  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>參數  
 `pSite`  
 指向控制項站台將要就地啟動。  
  
### <a name="remarks"></a>備註  
 在就地啟用表示容器的主功能表取代就地組合功能表。  
  
##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate  
 由架構呼叫時，控制站台所指`pSite`，即將停用。  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>參數  
 `pSite`  
 指向控制項站台即將關閉。  
  
### <a name="remarks"></a>備註  
 收到此通知時，容器應重新安裝它的使用者介面，並取得焦點。  
  
##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren  
 從子視窗接收捲動訊息時由架構呼叫。  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>參數  
 `dx`  
 沿著 x 軸的捲動的數量，以像素。  
  
 *dy*  
 沿著 y 軸的捲動的數量，以像素。  
  
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
 `nID`  
 指定接收訊息之控制項的識別碼。  
  
 `message`  
 指定要傳送的訊息。  
  
 `wParam`  
 指定特定訊息的其他資訊。  
  
 `lParam`  
 指定特定訊息的其他資訊。  
  
##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt  
 設定控制項的文字，在對話方塊中指定的整數值的字串表示法。  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制項的識別項。  
  
 `nValue`  
 要顯示的整數值。  
  
 `bSigned`  
 指定是否`nValue`參數已簽署或不帶正負號。 如果這個參數是**TRUE**，`nValue`簽署。 如果這個參數是**TRUE**和`nValue`小於零，字串中的第一個數字之前放置登減號。 如果這個參數是**FALSE**，`nValue`不帶正負號。  
  
##  <a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText  
 設定指定的控制項，使用中包含的文字的文字`lpszString`。  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 控制項的識別項。  
  
 `lpszString`  
 控制項的文字指標。  
  
## <a name="see-also"></a>請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager 類別](../../mfc/reference/coccmanager-class.md)
