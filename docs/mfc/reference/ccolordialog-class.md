---
title: CColorDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
dev_langs:
- C++
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3888f054baab61bb7422403b0766d7f757914d1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ccolordialog-class"></a>CColorDialog 類別
可讓您將色彩選取對話方塊中併入您的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|建構 `CColorDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|會顯示一個對話方塊，可讓使用者進行選取。|  
|[CColorDialog::GetColor](#getcolor)|傳回**COLORREF**結構，包含選取之色彩的值。|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|擷取使用者所建立的自訂色彩。|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|會強制將目前的色彩選擇，以指定的色彩。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|覆寫，以驗證輸入對話方塊中的色彩。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|結構，用來自訂對話方塊的設定。|  
  
## <a name="remarks"></a>備註  
 A`CColorDialog`物件是針對顯示系統定義的色彩清單對話方塊。 使用者可以選取，或從清單中，會再回報給應用程式結束對話方塊時，建立以特定色彩。  
  
 若要建構`CColorDialog`物件、 使用提供的建構函式或衍生新類別，並使用您自己的自訂建構函式。  
  
 一旦建構的對話方塊中，您可以設定或修改中的任何值[m_cc](#m_cc)結構，以初始化對話方塊的控制項的值。 `m_cc`結構的類型是[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 初始化對話方塊的控制項之後呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者選取色彩。 `DoModal` 傳回使用者的選取項目中的其中一個對話方塊的 [確定] ( **IDOK**) 或 [取消] ( **IDCANCEL**) 按鈕。  
  
 如果`DoModal`傳回**IDOK**，您可以使用其中一個`CColorDialog`的成員函式來擷取使用者輸入的資訊。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式判斷是否在對話方塊的初始化期間發生錯誤，並深入了解錯誤。  
  
 `CColorDialog` 依賴 COMMDLG。隨附於 Windows 版本 3.1 和更新版本的 DLL 檔案。  
  
 若要自訂對話方塊中，衍生自`CColorDialog`，提供自訂對話方塊範本中，加入處理從擴充的控制項通知訊息的訊息對應。 任何未處理的訊息應該傳遞至基底類別。  
  
 自訂攔截函式不需要。  
  
> [!NOTE]
>  在某些安裝`CColorDialog`物件將不會顯示灰色背景如果您已使用架構來進行其他`CDialog`物件灰色。  
  
 如需有關使用`CColorDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdlgs.h  
  
##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog  
 建構 `CColorDialog` 物件。  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *clrInit*  
 預設的色彩選擇。 如果未不指定任何值，則預設為 RGB(0,0,0) （黑色）。  
  
 `dwFlags`  
 一組自訂函式和對話方塊外觀的旗標。 如需詳細資訊，請參閱[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830) Windows SDK 中的結構。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CColorDialog::DoModal  
 呼叫此函式可顯示 Windows 通用色彩對話方塊中，並且允許使用者選取色彩。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是傳回，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 **IDOK**和**IDCANCEL**是常數，以指出使用者是否選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種色彩對話方塊選項[m_cc](#m_cc)結構，您應該這麼做會在呼叫之前`DoModal`但在建構對話方塊物件之後。  
  
 在呼叫`DoModal`，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者資訊輸入。  
  
### <a name="example"></a>範例  
  請參閱範例的[CColorDialog::CColorDialog](#ccolordialog)。  
  
##  <a name="getcolor"></a>  CColorDialog::GetColor  
 呼叫此函式之後呼叫`DoModal`擷取使用者選取的色彩資訊。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊的值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors  
 `CColorDialog` 物件，允許使用者，除了選取色彩，定義自訂色彩，最多 16 個。  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>傳回值  
 儲存使用者所建立的自訂色彩 16 RGB 色彩值的陣列指標。  
  
### <a name="remarks"></a>備註  
 `GetSavedCustomColors`成員函式提供存取這些色彩。 之後，就可以擷取這些色彩[DoModal](#domodal)傳回**IDOK**。  
  
 每個傳回之陣列中 16 的 RGB 值會初始化為 RGB(255,255,255) （白色）。 只在應用程式中的 [對話方塊] 方塊引動過程之間，會儲存使用者選擇自訂色彩。 如果您想要儲存這些應用程式的引動過程之間的色彩，您必須儲存它們以其他方式，例如在初始化期間 (。INI) 檔案。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>  CColorDialog::m_cc  
 型別的結構[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)，其成員儲存的特性和對話方塊中的值。  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>備註  
 之後建構`CColorDialog`物件，您可以使用`m_cc`設定對話方塊中，會在呼叫之前的各個層面[DoModal](#domodal)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>  CColorDialog::OnColorOK  
 覆寫，以驗證輸入對話方塊中的色彩。  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果不應關閉對話方塊。否則為 0 表示接受輸入的色彩。  
  
### <a name="remarks"></a>備註  
 只有當您想要提供自訂驗證的使用者選取色彩對話方塊中的色彩，請覆寫這個函式。  
  
 使用者可以選取色彩，由下列兩種方法之一：  
  
-   按一下色彩調色盤的色彩。 所選取之色彩的 RGB 值然後會反映在適當的 RGB 編輯方塊中。  
  
-   輸入 RGB 值的編輯方塊  
  
 覆寫`OnColorOK`可讓您拒絕使用者通用的 [色彩] 對話方塊中輸入任何應用程式特定原因的色彩。  
  
 一般來說，您不需要使用此函式，因為架構提供的色彩的預設驗證，並顯示訊息方塊，如果輸入無效的色彩。  
  
 您可以呼叫[SetCurrentColor](#setcurrentcolor)從`OnColorOK`強制色彩選擇。 一次`OnColorOK`已經引發 (亦即，使用者按一下 **[確定]** 接受變更的色彩)，您可以呼叫[GetColor](#getcolor)取得新的色彩的 RGB 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor  
 呼叫此函式之後呼叫`DoModal`強制中指定的色彩值目前的色彩選擇`clr`。  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
 訊息處理常式中呼叫此函式或`OnColorOK`。 對話方塊會自動更新的值為基礎的使用者選取`clr`參數。  
  
### <a name="example"></a>範例  
  請參閱範例的[CColorDialog::OnColorOK](#oncolorok)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../visual-cpp-samples.md)   
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)

