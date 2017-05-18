---
title: "COlePropertiesDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- OLE Object Properties dialog box
- Object Properties dialog box
- dialog boxes, OLE
- OLE documents, modifying properties
- property pages, OLE
- COlePropertiesDialog class
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 1a53c1e65504049e35fdec8065de279ca41fe342
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog 類別
封裝 Windows 通用 OLE 物件屬性對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|建構 `COlePropertiesDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選取。|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|調整文件項目變更時由架構呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|結構，用來初始化的 [一般] 頁面`COlePropertiesDialog`物件。|  
|[COlePropertiesDialog::m_lp](#m_lp)|結構，用來初始化的 「 連結 」 頁面`COlePropertiesDialog`物件。|  
|[COlePropertiesDialog::m_op](#m_op)|結構，用來初始化`COlePropertiesDialog`物件。|  
|[COlePropertiesDialog::m_psh](#m_psh)|結構，用來新增額外的自訂屬性頁。|  
|[COlePropertiesDialog::m_vp](#m_vp)|結構，用於自訂的 「 檢視 」 頁面`COlePropertiesDialog`物件。|  
  
## <a name="remarks"></a>備註  
 通用 OLE 物件屬性對話方塊提供簡單的方式來顯示和修改 OLE 文件項目與 Windows 標準一致的方式的屬性。 這些屬性包括和其他項目，在文件項目，顯示圖示和影像縮放比例，和選項資訊的項目連結 （如果連結的項目） 所表示的檔案上的資訊。  
  
 若要使用`COlePropertiesDialog`物件，請先建立物件使用`COlePropertiesDialog`建構函式。 在建構對話方塊之後，呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者修改項目的任何屬性。 `DoModal`傳回使用者是否選取 [確定] ( **IDOK**) 或 [取消] ( **IDCANCEL**) 按鈕。 除了 確定 和 取消 按鈕時，沒有套用 按鈕。 當使用者選取 [套用] 時，文件項目的屬性所做的變更會套用至項目和其映像會自動更新，但仍在進行中。  
  
 [M_psh](#m_psh)資料成員是一個指向**PROPSHEETHEADER**結構，且大部分情況下，您不需要明確存取權限。 有一個例外狀況時，您需要預設的一般、 檢視和連結頁面之外的其他屬性頁。 在此情況下，您可以修改`m_psh`資料成員，以包含您自訂的網頁，然後再呼叫`DoModal`成員函式。  
  
 如需有關 OLE 對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog  
 建立 `COlePropertiesDialog` 物件。  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 目前正在存取其屬性的文件項目的指標。  
  
 *nScaleMin*  
 最小縮放比例百分比為文件項目影像。  
  
 *nScaleMax*  
 最大縮放比例百分比為文件項目影像。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者的指標。  
  
### <a name="remarks"></a>備註  
 衍生您通用 OLE 物件屬性的對話方塊類別從`COlePropertiesDialog`為了實作調整您的文件項目。 任何藉由這個類別的執行個體 對話方塊將不支援縮放比例的文件項目。  
  
 根據預設，通用 OLE 物件屬性對話方塊中會有三個預設頁面︰  
  
-   一般  
  
     此頁面包含所選取的文件項目表示的檔案系統資訊。 從這個頁面上，使用者可以將選取的項目轉換成另一種類型。  
  
-   檢視  
  
     此頁面包含顯示項目、 變更圖示，以及變更影像的縮放選項。  
  
-   連結  
  
     此頁面包含變更的連結項目位置及更新連結的項目選項。 從這個頁面上，使用者可能會中斷選取之項目的連結。  
  
 若要將頁面之外，提供依預設，修改[m_psh](#m_psh)結束的建構函式之前的成員變數您`COlePropertiesDialog`-衍生的類別。 這是進階的實作`COlePropertiesDialog`建構函式。  
  
##  <a name="domodal"></a>COlePropertiesDialog::DoModal  
 呼叫此成員函式，以顯示 Windows 通用 OLE 物件屬性對話方塊中，並允許使用者檢視及/或變更文件項目中的各種屬性。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**如果成功，則為，否則為 0。 **IDOK**和**IDCANCEL**是常數，以指出使用者是否選取 [確定] 或 [取消] 按鈕。  
  
 如果**IDCANCEL**傳回時，您可以呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
##  <a name="m_gp"></a>COlePropertiesDialog::m_gp  
 型別的結構[OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)，用來初始化 OLE 物件屬性] 對話方塊的 [一般] 頁面。  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>備註  
 此頁面顯示的類型和大小的內嵌，並可讓使用者存取 [轉換] 對話方塊。 此頁面也會顯示連結目的地的物件是否連結。  
  
 如需有關**OLEUIGNRLPROPS**結構，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_lp"></a>COlePropertiesDialog::m_lp  
 型別的結構[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)，用來初始化 OLE 物件屬性] 對話方塊的 [連結] 頁面。  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>備註  
 此頁面會顯示連結項目的位置，並可讓使用者更新，或中斷，項目的連結。  
  
 如需有關**OLEUILINKPROPS**結構，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_op"></a>COlePropertiesDialog::m_op  
 型別的結構[OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199)，用來初始化通用 OLE 物件屬性對話方塊。  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>備註  
 此結構包含用來初始化一般、 連結和檢視頁面的成員。  
  
 如需詳細資訊，請參閱**OLEUIOBJECTPROPS**和[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_psh"></a>COlePropertiesDialog::m_psh  
 型別的結構[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)，其成員儲存對話方塊物件的特性。  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>備註  
 之後建構`COlePropertiesDialog`物件，您可以使用`m_psh`設定對話方塊中，會在呼叫之前的各個層面`DoModal`成員函式。  
  
 如果您修改`m_psh`資料成員直接管理，您將會覆寫任何預設行為。  
  
 如需有關**PROPSHEETHEADER**結構，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_vp"></a>COlePropertiesDialog::m_vp  
 型別的結構[OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)，用來初始化 OLE 物件屬性] 對話方塊的 [檢視] 頁面。  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>備註  
 此頁面可讓使用者切換 「 內容 」 和 「 圖示 」 檢視的物件，並變更其調整容器內。 物件會顯示為圖示時，它也可讓使用者存取 [變更圖示] 對話方塊。  
  
 如需有關**OLEUIVIEWPROPS**結構，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale  
 縮放比例的值已變更，並選取 確定 或 套用時由架構呼叫。  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 目前正在存取其屬性的文件項目的指標。  
  
 `nCurrentScale`  
 對話方塊標尺的數值。  
  
 *bRelativeToOrig*  
 指出是否調整套用至文件項目的原始大小。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已處理。否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 您必須覆寫此函式可啟用縮放控制項。  
  
> [!NOTE]
>  通用 OLE 物件屬性對話方塊中顯示之前，架構會呼叫這個函式**NULL**如`pItem`，-1 表示`nCurrentScale`。 這是為了判斷是否應該啟用縮放控制項。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CIRC](../../visual-cpp-samples.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage 類別](../../mfc/reference/cpropertypage-class.md)

