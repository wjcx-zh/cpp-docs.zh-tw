---
title: "CMFCColorDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc8b547b72a7094bb6337e9e412f8548a48820f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 類別
`CMFCColorDialog`類別代表色彩選取對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|建構 `CMFCColorDialog` 物件。|  
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|傳回目前選取的色彩。|  
|[CMFCColorDialog::GetPalette](#getpalette)|傳回色彩的調色盤。|  
|`CMFCColorDialog::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需語法和詳細資訊，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CDialogEx::PreTranslateMessage`。)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|從系統調色盤來衍生調色盤。|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|設定目前選取的色彩。|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|設定最相當於指定的 RGB 值的色彩。|  
|[CMFCColorDialog::SetPageOne](#setpageone)|選取第一個屬性頁的 RGB 值。|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|選取第二個屬性頁的 RGB 值。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`如果色彩選取對話方塊使用自己的色彩調色盤，或`FALSE`如果對話方塊中，將會使用調色盤中指定`CMFCColorDialog`建構函式。|  
|`m_bPickerMode`|`TRUE`當使用者從選取範圍 對話方塊中，選取一個色彩否則， `FALSE`。|  
|`m_btnColorSelect`|使用者選取的色彩按鈕。|  
|`m_CurrentColor`|目前選取的色彩。|  
|`m_hcurPicker`|資料指標用來選擇色彩。|  
|`m_NewColor`|潛在所選取之色彩，可以永久選取或已還原成原始的色彩。|  
|`m_pColourSheetOne`|色彩選取範圍的屬性工作表的第一個屬性頁指標。|  
|`m_pColourSheetTwo`|第二個屬性頁色彩選取範圍的屬性工作表的指標。|  
|`m_pPalette`|目前的邏輯色板。|  
|`m_pPropSheet`|色彩選取對話方塊的屬性工作表指標。|  
|`m_wndColors`|色彩選擇器控制項物件。|  
|`m_wndStaticPlaceHolder`|這是一個預留位置，色彩選擇器內容工作表頁靜態控制項。|  
  
## <a name="remarks"></a>備註  
 色彩選取對話方塊會顯示為具有兩個頁面的屬性工作表。 在第一個頁面上，您必須選取標準色彩從系統調色盤。在第二個頁面上，您可以選取自訂色彩。  
  
 您可以建構`CMFCColorDialog`堆疊上的物件，然後呼叫`DoModal`，當做參數傳遞的初始色彩`CMFCColorDialog`建構函式。 色彩選取對話方塊接著會建立數個[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)物件來處理每個色彩調色盤。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法來設定色彩對話方塊`CMFCColorDialog`類別。 此範例示範如何設定目前和新的色彩 對話方塊中，以及如何在兩個屬性頁的 色彩 對話方塊上設定所選色彩的紅色、 綠色和藍色元件。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcolordialog.h  
  
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
 [輸入] `clrInit`  
 預設的色彩選擇。 如果未不指定任何值，則預設為 RGB(0,0,0) （黑色）。  
  
 [輸入] `dwFlags`  
 （保留）。  
  
 [輸入] `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。  
  
 [輸入] `hPal`  
 色彩調色盤的控制代碼。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 擷取使用者從 [色彩] 對話方塊中選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊的值。  
  
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
 色彩調色盤，指定使用者可以選擇的色彩。  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 從系統調色盤來衍生調色盤。  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 設定目前的色彩 對話方塊。  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rgb`  
 RGB 色彩值  
  
### <a name="remarks"></a>備註  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 將目前的色彩設定為目前是最相似的調色盤的色彩。  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rgb`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)指定 RGB 色彩。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 色彩對話方塊的第一個屬性頁面上會明確指定所選色彩的紅色、 綠色和藍色元件。  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `R`  
 指定 RGB 值的紅色元件。  
  
 [輸入] `G`  
 指定 RGB 值的綠色元件。  
  
 [輸入] `B`  
 指定 RGB 值的藍色元件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 在色彩對話方塊的第二個屬性頁上會明確指定所選色彩的紅色、 綠色和藍色元件。  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `R`  
 指定 RGB 值的紅色的元件  
  
 [輸入] `G`  
 指定 RGB 值的綠色的元件  
  
 [輸入] `B`  
 指定 RGB 值的藍色的元件  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)
