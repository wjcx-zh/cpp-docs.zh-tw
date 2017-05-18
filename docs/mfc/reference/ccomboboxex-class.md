---
title: "CComboBoxEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes, CComboBoxEx class
- Windows common controls [C++], extended combo boxes
- common controls [C++], extended combo boxes
- combo boxes [C++], CComboBoxEx class
- Internet Explorer 4.0 common controls
- CComboBoxEx class
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e88ed701111b49e3a5d3b32868bfad8e77206086
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomboboxex-class"></a>CComboBoxEx 類別
藉由提供影像清單的支援，擴充下拉式方塊控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|建構 `CComboBoxEx` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComboBoxEx::Create](#create)|建立下拉式方塊，並將它附加`CComboBoxEx`物件。|  
|[CComboBoxEx::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立下拉式方塊，並附加至該**ComboBoxEx**物件。|  
|[CComboBoxEx::DeleteItem](#deleteitem)|移除項目從**ComboBoxEx**控制項。|  
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|擷取子下拉式方塊控制項的指標。|  
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|擷取的編輯控制項部分的控制代碼**ComboBoxEx**控制項。|  
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|擷取使用中的延伸的樣式**ComboBoxEx**控制項。|  
|[CComboBoxEx::GetImageList](#getimagelist)|擷取映像清單中，指派給指標**ComboBoxEx**控制項。|  
|[CComboBoxEx::GetItem](#getitem)|擷取項目資訊指定**ComboBoxEx**項目。|  
|[CComboBoxEx::HasEditChanged](#haseditchanged)|判斷使用者是否已變更的內容**ComboBoxEx** edit 控制項的輸入。|  
|[CComboBoxEx::InsertItem](#insertitem)|將新的項目中插入**ComboBoxEx**控制項。|  
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|設定延伸的樣式內**ComboBoxEx**控制項。|  
|[CComboBoxEx::SetImageList](#setimagelist)|設定的影像清單**ComboBoxEx**控制項。|  
|[CComboBoxEx::SetItem](#setitem)|設定的屬性中的項目**ComboBoxEx**控制項。|  
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|設定之視覺樣式的擴充的下拉式方塊控制項。|  
  
## <a name="remarks"></a>備註  
 使用`CComboBoxEx`建立下拉式方塊控制項，您不再需要實作您自己的影像繪圖程式碼。 請改用`CComboBoxEx`存取映像從影像清單。  
  
## <a name="image-list-support"></a>影像清單的支援  
 在標準下拉式方塊中，下拉式方塊的擁有者負責建立主控描繪控制項下拉式方塊中繪製影像。 當您使用`CComboBoxEx`，您不需要設定的繪製樣式**CBS_OWNERDRAWFIXED**和**CBS_HASSTRINGS**因為它們隱含。 否則，您必須撰寫程式碼來執行繪製作業。 A`CComboBoxEx`控制項支援最多三個映像，每個項目︰ 一個用於已選取的狀態，如未選取狀態，其中一個，一個用於覆疊影像。  
  
## <a name="styles"></a>樣式  
 `CComboBoxEx`支援樣式**CBS_SIMPLE**， **CBS_DROPDOWN**， **CBS_DROPDOWNLIST**，和**WS_CHILD**。 控制要忽略所有其他傳遞時建立視窗的樣式。 在建立視窗之後，您可以提供其他下拉式方塊樣式藉由呼叫`CComboBoxEx`成員函式[SetExtendedStyle](#setextendedstyle)。 使用這些樣式，您可以︰  
  
-   設定字串搜尋區分大小寫清單中。  
  
-   建立下拉式方塊控制項，會使用斜線 （'/')、 反斜線 ('\\')，以及期間 ('。 ') 做為 word 分隔符號的字元。 這讓使用者跳斷字，使用鍵盤快速鍵 CTRL + 箭號。  
  
-   設定下拉式方塊控制項來顯示或不會顯示映像。 如果不會顯示影像，下拉式方塊可以移除映像所能容納的文字縮排。  
  
-   建立窄下拉式方塊控制項，包括讓該剪輯較寬的下拉式方塊包含調整大小。  
  
 這些樣式旗標會更進一步的說明[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## <a name="item-retention-and-callback-item-attributes"></a>保留項目和回呼項目屬性  
 項目資訊，例如索引項目和影像、 縮排的值及文字字串會儲存在 Win32 結構[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此結構也包含對應到回呼旗標的成員。  
  
 如需詳細的概念性的討論，請參閱[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx  
 呼叫此成員函式建立`CComboBoxEx`物件。  
  
```  
CComboBoxEx();
```  
  
##  <a name="create"></a>CComboBoxEx::Create  
 建立下拉式方塊，並將它附加`CComboBoxEx`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定套用至下拉式方塊的下拉式方塊樣式的組合。 請參閱**備註**如下如需有關樣式。  
  
 `rect`  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是位置和下拉式方塊的大小。  
  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)下拉式方塊的父視窗物件 (通常是`CDialog`)。 它不得為**NULL**。  
  
 `nID`  
 指定下拉式方塊控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 非零，如果物件建立成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 建立`CComboBoxEx`物件中的兩個步驟︰  
  
1.  呼叫[CComboBoxEx](#ccomboboxex)建構`CComboBoxEx`物件。  
  
2.  呼叫此成員函式，它會建立延伸的 Windows 下拉式方塊，然後將它附加`CComboBoxEx`物件。  
  
 當您呼叫**建立**，MFC 初始化通用控制項。  
  
 當您建立下拉式方塊時，您可以指定任何或所有下列下拉式方塊樣式︰  
  
- **CBS_SIMPLE**  
  
- **CBS_DROPDOWN**  
  
- **CBS_DROPDOWNLIST**  
  
- **CBS_AUTOHSCROLL**  
  
- **WS_CHILD**  
  
 會忽略所有其他傳遞時建立視窗的樣式。 **ComboBoxEx**控制項也支援提供的額外功能的延伸的樣式。 這些樣式中所述[ComboBoxEx 控制延伸的樣式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 藉由呼叫設定這些樣式[SetExtendedStyle](#setextendedstyle)。  
  
 如果您想要使用延伸的視窗樣式與您的控制項，呼叫[CreateEx](#createex)而不是**建立**。  
  
##  <a name="createex"></a>CComboBoxEx::CreateEx  
 呼叫此函式可建立擴充的下拉式方塊控制項 （子視窗），並將它與關聯`CComboBoxEx`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 下拉式方塊控制項的樣式。 請參閱[建立](#create)樣式的清單。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是**建立**套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
 `CreateEx`建立具有所指定的延伸視窗樣式控制項`dwExStyle`。 您必須將延伸的樣式特定擴充的下拉式方塊控制項中使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`設為這類樣式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`設為這類樣式**CBES_EX_CASESENSITIVE**。 如需詳細資訊，請參閱本主題中所述的樣式[ComboBoxEx 控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="deleteitem"></a>CComboBoxEx::DeleteItem  
 移除項目從**ComboBoxEx**控制項。  
  
```  
int DeleteItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 要移除之項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 在控制項中剩餘的項目數目。 如果`iIndex`是無效的則函數會傳回**CB_ERR**。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的訊息功能[CBEM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb775768)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 當您呼叫 DeleteItem [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)訊息**CBEN_DELETEITEM**會傳送通知給父視窗。  
  
##  <a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl  
 呼叫此成員函式內的下拉式方塊控制項中取得的指標`CComboBoxEx`物件。  
  
```  
CComboBox* GetComboBoxCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CComboBox`物件。  
  
### <a name="remarks"></a>備註  
 `CComboBoxEx`控制項組成父視窗，其中封裝`CComboBox`。  
  
 `CComboBox`所指之傳回值的物件是暫存物件，並且被終結在下一步的閒置處理時間。  
  
##  <a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl  
 呼叫此成員函式來取得編輯控制項下拉式方塊的指標。  
  
```  
CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CEdit](../../mfc/reference/cedit-class.md)物件。  
  
### <a name="remarks"></a>備註  
 A`CComboBoxEx`控制項使用的編輯方塊，在建立時**CBS_DROPDOWN**樣式。  
  
 `CEdit`所指之傳回值的物件是暫存物件，並且被終結在下一步的閒置處理時間。  
  
##  <a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle  
 呼叫此成員函式，以取得用來延伸的樣式`CComboBoxEx`控制項。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `DWORD`值，其中包含用於下拉式方塊控制項的延伸的樣式。  
  
### <a name="remarks"></a>備註  
 請參閱[ComboBoxEx 控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關這些樣式。  
  
##  <a name="getimagelist"></a>CComboBoxEx::GetImageList  
 呼叫此成員函式所使用的影像清單中取得的指標`CComboBoxEx`控制項。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。 如果失敗，此成員函式會傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 `CImageList`所指之傳回值的物件是暫存物件，並且被終結在下一步的閒置處理時間。  
  
##  <a name="getitem"></a>CComboBoxEx::GetItem  
 擷取項目資訊指定**ComboBoxEx**項目。  
  
```  
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>參數  
 `pCBItem`  
 指標[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)結構，將會收到項目資訊。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的訊息功能[CBEM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775779)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="haseditchanged"></a>CComboBoxEx::HasEditChanged  
 判斷使用者是否已變更的內容**ComboBoxEx** edit 控制項的輸入。  
  
```  
BOOL HasEditChanged();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用者輸入控制項的編輯方塊。否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的訊息功能[CBEM_HASEDITCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb775782)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="insertitem"></a>CComboBoxEx::InsertItem  
 將新的項目中插入**ComboBoxEx**控制項。  
  
```  
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>參數  
 `pCBItem`  
 指標[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)結構，將會收到項目資訊。 此結構包含項目的回呼旗標值。  
  
### <a name="return-value"></a>傳回值  
 此時如果成功;，已插入新項目索引否則為-1。  
  
### <a name="remarks"></a>備註  
 當您呼叫`InsertItem`、 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)訊息[CBEN_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb775764)會傳送通知給父視窗。  
  
##  <a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle  
 呼叫此成員函式設定用於擴充控制項的下拉式方塊的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,  
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>參數  
 `dwExMask`  
 A`DWORD`值，指出在哪些樣式`dwExStyles`會受到影響。 只有在延伸的樣式`dwExMask`將會變更。 因為將保留所有其他樣式。 如果此參數為零，則所有在樣式`dwExStyles`會受到影響。  
  
 `dwExStyles`  
 A`DWORD`值，其中包含下拉式方塊控制項來設定控制項的延伸的樣式。  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`值，其中包含先前用於控制項的延伸的樣式。  
  
### <a name="remarks"></a>備註  
 請參閱[ComboBoxEx 控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關這些樣式。  
  
 若要建立擴充具有延伸的視窗樣式控制項的下拉式方塊，請使用[CreateEx](#createex)。  
  
##  <a name="setimagelist"></a>CComboBoxEx::SetImageList  
 設定的影像清單**ComboBoxEx**控制項。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標`CImageList`物件，其中包含要使用的映像`CComboBoxEx`控制項。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，其中包含先前所使用的影像`CComboBoxEx`控制項。 **NULL**如果先前已經不設定任何映像清單。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的訊息功能[CBEM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775787)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果您變更預設編輯控制項的高度，呼叫 Win32 函式[SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545)調整控制項的大小之後您呼叫, `SetImageList`，或無法正常顯示。  
  
 `CImageList`所指之傳回值的物件是暫存物件，並且被終結在下一步的閒置處理時間。  
  
##  <a name="setitem"></a>CComboBoxEx::SetItem  
 設定的屬性中的項目**ComboBoxEx**控制項。  
  
```  
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>參數  
 `pCBItem`  
 指標[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)結構，將會收到項目資訊。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的訊息功能[CBEM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775788)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme  
 設定之視覺樣式的擴充的下拉式方塊控制項。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>參數  
 `pszSubAppName`  
 Unicode 字串，包含擴充的下拉式方塊視覺化樣式，來設定指標。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[CBEM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb775790)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCIE](../../visual-cpp-samples.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)

