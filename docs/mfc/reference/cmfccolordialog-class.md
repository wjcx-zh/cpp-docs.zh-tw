---
title: "CMFCColorDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog::m_CurrentColor data member
- CMFCColorDialog::m_pPropSheet data member
- CMFCColorDialog::m_btnColorSelect data member
- CMFCColorDialog class
- CMFCColorDialog::m_wndColors data member
- CMFCColorDialog::m_bIsMyPalette data member
- CMFCColorDialog::m_pColourSheetTwo data member
- CMFCColorDialog::m_NewColor data member
- CMFCColorDialog::m_pPalette data member
- CMFCColorDialog::m_wndStaticPlaceHolder data member
- CMFCColorDialog::m_pColourSheetOne data member
- CMFCColorDialog::m_hcurPicker data member
- CMFCColorDialog::PreTranslateMessage method
- CMFCColorDialog::m_bPickerMode data member
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
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
ms.openlocfilehash: ac621157e0fcb5bcabef2ae8f367a1b141b4ace0
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 類別
`CMFCColorDialog`類別表示色彩選取對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|建構 `CMFCColorDialog` 物件。|  
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|傳回目前選取的色彩。|  
|[CMFCColorDialog::GetPalette](#getpalette)|傳回的色彩調色盤。|  
|`CMFCColorDialog::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需語法和詳細資訊，請參閱[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CDialogEx::PreTranslateMessage`。)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|調色盤會衍生自系統調色盤。|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|設定目前選取的色彩。|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|設定色彩最相當於指定的 RGB 值。|  
|[CMFCColorDialog::SetPageOne](#setpageone)|選取第一個內容頁的 RGB 值。|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|選取第二個屬性頁的 RGB 值。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`如果色彩選取對話方塊中使用它自己的調色盤，或`FALSE`如果對話方塊中，將會使用調色盤中指定`CMFCColorDialog`建構函式。|  
|`m_bPickerMode`|`TRUE`當使用者從選取範圍 對話方塊中，選取一個色彩否則， `FALSE`。|  
|`m_btnColorSelect`|使用者選取 [色彩] 按鈕。|  
|`m_CurrentColor`|目前選取的色彩。|  
|`m_hcurPicker`|用來挑選色彩的資料指標。|  
|`m_NewColor`|潛在選取的色彩，可以永久選取或已還原成原始的色彩。|  
|`m_pColourSheetOne`|第一個內容頁色彩選取項目屬性工作表的指標。|  
|`m_pColourSheetTwo`|第二個屬性頁色彩選取項目屬性工作表的指標。|  
|`m_pPalette`|目前的邏輯調色盤。|  
|`m_pPropSheet`|色彩選取對話方塊的屬性工作表指標。|  
|`m_wndColors`|色彩選擇器控制項物件。|  
|`m_wndStaticPlaceHolder`|靜態控制項的色彩選擇器的屬性工作表的預留位置。|  
  
## <a name="remarks"></a>備註  
 色彩選取對話方塊會顯示為兩個頁面將屬性工作表。 在第一個頁面上，您的標準色彩從調色盤中選取系統。在第二個頁面上，您可以選取自訂色彩。  
  
 您可以建構`CMFCColorDialog`物件在堆疊上，然後呼叫`DoModal`，做為參數傳遞的初始色彩`CMFCColorDialog`建構函式。 色彩選取對話方塊接著會建立數個[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)物件來處理每個色彩調色盤。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的設定色彩對話方塊`CMFCColorDialog`類別。 此範例示範如何設定目前和新的色彩 對話方塊中，以及如何設定兩個屬性頁面上的 色彩 對話方塊中選取之色彩的紅色、 綠色和藍色元件。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&3;](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 建構 `CMFCColorDialog` 物件。  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrInit`  
 預設色彩選項。 如果未不指定任何值，預設為 RGB(0,0,0) （黑色）。  
  
 [in] `dwFlags`  
 （保留）。  
  
 [in] `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。  
  
 [in] `hPal`  
 色彩調色盤的控制代碼。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 擷取使用者從 [色彩] 對話方塊中選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，其中包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後您呼叫,`DoModal`方法。  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 擷取目前的色彩 對話方塊中可用的色彩調色盤。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CPalette`中所指定的物件`CMFCColorDialog`建構函式。  
  
### <a name="remarks"></a>備註  
 色彩調色盤指定使用者可以選擇的色彩。  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 調色盤會衍生自系統調色盤。  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 設定目前的色彩 對話方塊。  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>參數  
 [in] `rgb`  
 RGB 色彩值  
  
### <a name="remarks"></a>備註  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 將目前的色彩設定為目前最類似的調色盤的色彩。  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>參數  
 [in] `rgb`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)指定 RGB 色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 第一個內容頁的 [色彩] 對話方塊上，明確地指定所選取之色彩的紅色、 綠色和藍色元件。  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>參數  
 [in] `R`  
 指定 RGB 值的紅色元件。  
  
 [in] `G`  
 指定 RGB 值的綠色元件。  
  
 [in] `B`  
 指定藍元件的 RGB 值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 第二個屬性頁的 [色彩] 對話方塊上，明確地指定所選取之色彩的紅色、 綠色和藍色元件。  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>參數  
 [in] `R`  
 指定 RGB 值的紅色的元件  
  
 [in] `G`  
 指定 RGB 值的綠色的元件  
  
 [in] `B`  
 指定 RGB 值的藍色的元件  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)

