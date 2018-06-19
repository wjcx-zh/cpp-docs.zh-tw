---
title: CStatic 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3b1a5dcfc8481727bffd8b80e0bb1b230d56ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375000"
---
# <a name="cstatic-class"></a>CStatic 類別
提供 Windows 靜態控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|建構 `CStatic` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStatic::Create](#create)|建立 Windows 靜態控制項，並將它附加至`CStatic`物件。|  
|[CStatic::DrawItem](#drawitem)|覆寫，以繪製主控描繪靜態控制項。|  
|[CStatic::GetBitmap](#getbitmap)|擷取與先前設定之點陣圖的控制代碼[SetBitmap](#setbitmap)。|  
|[CStatic::GetCursor](#getcursor)|與先前設定的資料指標影像的控制代碼的擷取[SetCursor](#setcursor)。|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|擷取與先前設定的增強型中繼檔的控制代碼[SetEnhMetaFile](#setenhmetafile)。|  
|[CStatic::GetIcon](#geticon)|擷取圖示與先前設定的控制代碼[SetIcon](#seticon)。|  
|[CStatic::SetBitmap](#setbitmap)|指定要在靜態控制項中顯示的點陣圖。|  
|[CStatic::SetCursor](#setcursor)|指定要在靜態控制項中顯示的游標映像。|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要在靜態控制項中顯示增強型中繼檔。|  
|[CStatic::SetIcon](#seticon)|指定要在靜態控制項中顯示的圖示。|  
  
## <a name="remarks"></a>備註  
 靜態控制項顯示文字字串、 方塊、 矩形、 圖示、 游標、 點陣圖或增強型中繼檔。 它可以用來加上標籤，方塊中，或分隔其他控制項。 靜態控制項通常會接受任何輸入，並不提供任何輸出。不過，它可以通知其父代的滑鼠按鍵的情況下建立具有**SS_NOTIFY**樣式。  
  
 兩個步驟建立靜態控制項。 首先，呼叫建構函式來建構`CStatic`物件，然後呼叫[建立](#create)成員函式來建立靜態控制項，並將其附加至`CStatic`物件。  
  
 如果您建立`CStatic`物件 （透過對話方塊資源），對話方塊內`CStatic`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CStatic`物件內的視窗中，您可能也需要終結。 A`CStatic`即會自動終結視窗在堆疊上建立的物件。 如果您建立`CStatic`使用堆積上的物件**新**函式，您必須呼叫**刪除**與其完成時終結該物件上。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="create"></a>  CStatic::Create  
 建立 Windows 靜態控制項，並將它附加至`CStatic`物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 指定要放置在控制項中的文字。 如果**NULL**，不會顯示任何文字。  
  
 `dwStyle`  
 指定靜態控制項的視窗樣式。 套用的任何組合[靜態控制項樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles)至控制項。  
  
 `rect`  
 指定的位置和靜態控制項的大小。 它可以是`RECT`結構或`CRect`物件。  
  
 `pParentWnd`  
 指定`CStatic`父視窗，通常`CDialog`物件。 它不得為**NULL**。  
  
 `nID`  
 指定靜態控制項的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 建構`CStatic`兩個步驟中的物件。 首先，呼叫建構函式`CStatic`，然後呼叫**建立**，建立 Windows 靜態控制項，並將它附加至`CStatic`物件。  
  
 套用下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)靜態控制項：  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果您要顯示在靜態控制項的點陣圖、 游標、 圖示或中繼檔，您必須套用下列其中一種[靜態樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- **SS_BITMAP**點陣圖使用此樣式。  
  
- **SS_ICON**使用此樣式的資料指標和圖示。  
  
- **SS_ENHMETAFILE**對增強型中繼檔中使用此樣式。  
  
 資料指標、 點陣圖或圖示，您也可以使用下列樣式：  
  
- **SS_CENTERIMAGE**用於置中靜態控制項的影像。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>  CStatic::CStatic  
 建構 `CStatic` 物件。  
  
```  
CStatic();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CStatic::DrawItem  
 由架構呼叫以繪製主控描繪靜態控制項。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構。 此結構包含要繪製的項目和所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來實作繪圖的描繪**CStatic**物件 (控制項已樣式**SS_OWNERDRAW**)。  
  
##  <a name="getbitmap"></a>  CStatic::GetBitmap  
 取得點陣圖，使用先前設定的控制代碼[SetBitmap](#setbitmap)，也就是與相關聯`CStatic`。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為目前的點陣圖的控制代碼或**NULL**如果已不設定任何的點陣圖。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>  CStatic::GetCursor  
 取得游標處，使用先前設定的控制代碼[SetCursor](#setcursor)，也就是與相關聯`CStatic`。  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>傳回值  
 目前的資料指標的控制代碼或**NULL**如果已不設定任何資料指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile  
 取得與先前設定的增強型中繼檔的控制代碼[SetEnhMetafile](#setenhmetafile)，也就是與相關聯`CStatic`。  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的增強型中繼檔，控制代碼或**NULL**如果已設定無增強型中繼檔。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>  CStatic::GetIcon  
 取得圖示，並使用先前設定的控制代碼[SetIcon](#seticon)，也就是與相關聯`CStatic`。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在目前的圖示的控制代碼或**NULL**如果已設定無圖示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>  CStatic::SetBitmap  
 將新的點陣圖與靜態控制項產生關聯。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>參數  
 `hBitmap`  
 要在靜態控制項中繪製點陣圖的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 靜態控制項，先前關聯之點陣圖的控制代碼或`NULL`如果沒有點陣圖是與靜態控制項相關聯。  
  
### <a name="remarks"></a>備註  
 將會自動在靜態控制項中繪製了點陣圖。 根據預設，會被繪製在左上角和靜態控制項能調整大小的點陣圖。  
  
 您可以使用各種視窗和靜態控制項的樣式，包括：  
  
-   SS_BITMAP 一律使用此樣式的點陣圖。  
  
-   若要在靜態控制項中的影像置 SS_CENTERIMAGE 使用。 如果影像大於靜態控制項，則會裁剪。 如果是小於靜態控制項，在影像周圍的空白空間將會填入點陣圖的左上角像素的色彩。  
  
-   MFC 提供類別`CBitmap`，當您需要執行更多與點陣圖影像比直接呼叫 Win32 函式時，您可以使用`LoadBitmap`。 `CBitmap`其中包含一種 GDI 物件，通常會配合`CStatic`，也就是`CWnd`的用途顯示為靜態控制項的圖形物件的類別。  
  
 `CImage` 是 ATL/MFC 類別，可讓您更輕鬆地與裝置獨立點陣圖 (DIB)。 如需詳細資訊，請參閱[CImage 類別](../../atl-mfc-shared/reference/cimage-class.md)。  
  
-   通常是用來提供深度`CStatic::SetBitmap`HBITMAP 運算子所傳回的 GDI 物件`CBitmap`或`CImage`物件。 若要這樣做的程式碼類似下列的行。  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
下列範例會建立兩個`CStatic`堆積上的物件。 然後會載入其中一個系統點陣圖使用`CBitmap::LoadOEMBitmap`和其他檔案，使用`CImage::Load`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>  CStatic::SetCursor  
 將新的資料指標映像與靜態控制項產生關聯。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>參數  
 `hCursor`  
 要在靜態控制項中繪製游標的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 先前與靜態控制項相關聯的游標的控制代碼或**NULL**如果任何資料指標不是靜態控制項相關聯。  
  
### <a name="remarks"></a>備註  
 資料指標將會自動繪出，靜態控制項中。 根據預設，會被繪製在左上角和靜態控制項將會調整大小資料指標的大小。  
  
 您可以使用各種視窗和靜態控制項的樣式，包括下列：  
  
- **SS_ICON**一律使用此樣式，資料指標和圖示。  
  
- **SS_CENTERIMAGE** center 靜態控制項中使用。 如果影像大於靜態控制項，則會裁剪。 如果是小於靜態控制項，在影像周圍的空白空間將會填入靜態控制項的背景色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile  
 將新的增強型中繼檔映像與靜態控制項產生關聯。  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>參數  
 `hMetaFile`  
 要在靜態控制項中繪製的增強型中繼檔的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 之前與靜態控制項相關聯的增強型中繼檔的控制代碼或**NULL**如果沒有增強型中繼檔是與靜態控制項相關聯。  
  
### <a name="remarks"></a>備註  
 增強型中繼檔將會自動繪出，靜態控制項中。 增強型中繼檔會調整為適合靜態控制項的大小。  
  
 您可以使用各種視窗和靜態控制項的樣式，包括下列：  
  
- **SS_ENHMETAFILE**對增強型中繼檔一律使用此樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>  CStatic::SetIcon  
 將新的圖示影像與靜態控制項產生關聯。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 `hIcon`  
 要在靜態控制項中繪製圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 先前與靜態控制項相關聯的圖示的控制代碼或**NULL**是否與靜態控制項相關聯的圖示。  
  
### <a name="remarks"></a>備註  
 會在靜態控制項中會自動繪出圖示。 根據預設，會被繪製在左上角和靜態控制項將會調整大小圖示的大小。  
  
 您可以使用各種視窗和靜態控制項的樣式，包括下列：  
  
- **SS_ICON**一律使用此樣式，資料指標和圖示。  
  
- **SS_CENTERIMAGE** center 靜態控制項中使用。 如果影像大於靜態控制項，則會裁剪。 如果是小於靜態控制項，在影像周圍的空白空間將會填入靜態控制項的背景色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)
