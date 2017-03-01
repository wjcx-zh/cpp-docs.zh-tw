---
title: "CColorDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CColorDialog
dev_langs:
- C++
helpviewer_keywords:
- colors, dialog box
- dialog boxes, colors
- CColorDialog class
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: 25
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8aee088aadbca18acda348c574c8f4b55d1ecbb
ms.lasthandoff: 02/24/2017

---
# <a name="ccolordialog-class"></a>CColorDialog 類別
可讓您將色彩選取對話方塊納入應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|建構 `CColorDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|會顯示一個對話方塊，可讓使用者進行選擇。|  
|[CColorDialog::GetColor](#getcolor)|傳回**COLORREF**結構，其中包含所選取之色彩的值。|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|擷取使用者所建立的自訂色彩。|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|強制目前的色彩選擇，以指定的色彩。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|覆寫，以驗證輸入到對話方塊中的色彩。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|用來自訂設定，在對話方塊中的結構。|  
  
## <a name="remarks"></a>備註  
 A`CColorDialog`物件是針對顯示系統定義的色彩清單對話方塊。 使用者可以選取，或從清單中，然後回報給應用程式之對話方塊的 結束時建立特定的色彩。  
  
 若要建構`CColorDialog`物件、 使用提供的建構函式或衍生新類別，並使用您自己的自訂建構函式。  
  
 一旦建構的對話方塊中，您可以設定或修改中的任何值[m_cc](#m_cc)結構，以初始化對話方塊的控制項的值。 `m_cc`結構的型別是[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 初始化對話方塊的控制項之後, 呼叫`DoModal`成員函式來顯示對話方塊，並允許使用者選取的色彩。 `DoModal`傳回使用者的選取項目中的其中一個對話方塊的 確定 ( **IDOK**) 或 取消 ( **IDCANCEL**) 按鈕。  
  
 如果`DoModal`傳回**IDOK**，您可以使用其中一個`CColorDialog`的成員函式來擷取使用者輸入的資訊。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式判斷是否在對話方塊的初始化期間發生錯誤，並了解錯誤的詳細資訊。  
  
 `CColorDialog`依賴 COMMDLG。隨附於 Windows 3.1 和更新版本的 DLL 檔案。  
  
 若要自訂對話方塊中，衍生自`CColorDialog`、 提供自訂的對話方塊範本，以及新增訊息對應到處理從擴充的控制項通知訊息。 任何未處理的訊息應該傳遞至基底類別。  
  
 自訂攔截函式不需要。  
  
> [!NOTE]
>  某些安裝`CColorDialog`物件將不會顯示灰色背景如果您已使用架構來進行其他`CDialog`物件灰色。  
  
 如需有關使用`CColorDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdlgs.h  
  
##  <a name="a-nameccolordialoga--ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog  
 建構 `CColorDialog` 物件。  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *clrInit*  
 預設色彩選項。 如果未不指定任何值，預設為 RGB(0,0,0) （黑色）。  
  
 `dwFlags`  
 一組自訂的函式及外觀 對話方塊中的旗標。 如需詳細資訊，請參閱[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&49;](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="a-namedomodala--ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModal  
 呼叫此函式來顯示 Windows 通用色彩對話方塊中，並允許使用者選取色彩。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**會傳回，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 **IDOK**和**IDCANCEL**都是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化的各種色彩對話方塊選項[m_cc](#m_cc)結構，您應該執行這項操作之前，先呼叫`DoModal`但在建構對話方塊物件之後。  
  
 在呼叫`DoModal`，您可以呼叫其他成員函式來擷取設定或使用者的資訊輸入到對話方塊。  
  
### <a name="example"></a>範例  
  請參閱範例[CColorDialog::CColorDialog](#ccolordialog)。  
  
##  <a name="a-namegetcolora--ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor  
 呼叫此函式之後呼叫`DoModal`擷取使用者所選的色彩資訊。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，其中包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&50;](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="a-namegetsavedcustomcolorsa--ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors  
 `CColorDialog`物件可讓使用者，除了選擇色彩，來定義最多 16 個自訂色彩。  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>傳回值  
 儲存使用者所建立的自訂色彩 16 RGB 色彩值的陣列指標。  
  
### <a name="remarks"></a>備註  
 `GetSavedCustomColors`成員函式提供存取這些色彩。 之後，可以擷取這些色彩[DoModal](#domodal)傳回**IDOK**。  
  
 每個 16 RGB 值傳回的陣列中會初始化為 RGB(255,255,255) （白色）。 只會在應用程式中的對話方塊方塊引動過程之間，會儲存使用者選擇自訂色彩。 如果您想要儲存這些應用程式的引動過程之間的色彩，您必須儲存它們以其他方式，例如在初始化期間 (。INI) 檔案。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&51;](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="a-namemcca--ccolordialogmcc"></a><a name="m_cc"></a>CColorDialog::m_cc  
 型別的結構[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)，其成員儲存的特性和對話方塊中的值。  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>備註  
 在建構之後`CColorDialog`物件時，您可以使用`m_cc`設定 對話方塊中，然後再呼叫的各種層面[DoModal](#domodal)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&53;](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="a-nameoncoloroka--ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK  
 覆寫，以驗證輸入到對話方塊中的色彩。  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果不應該關閉對話方塊。否則為 0，表示接受輸入的色彩。  
  
### <a name="remarks"></a>備註  
 只有當您想要提供自訂驗證的使用者選取 [色彩] 對話方塊中的色彩，請覆寫這個函式。  
  
 使用者可以選取一個色彩，由下列兩種方法之一︰  
  
-   按一下色彩調色盤的色彩。 所選取之的色彩的 RGB 值接著會反映在適當的 RGB 編輯方塊中。  
  
-   輸入 RGB 值的編輯方塊  
  
 覆寫`OnColorOK`可讓您以拒絕使用者進入特定應用程式因故通用色彩對話方塊中的色彩。  
  
 一般來說，您不需要使用此函式，因為架構提供的色彩的預設驗證，並顯示訊息方塊，如果輸入無效的色彩。  
  
 您可以呼叫[SetCurrentColor](#setcurrentcolor)從`OnColorOK`強制色彩選擇。 一次`OnColorOK`已經引發 (亦即，使用者按一下**確定**接受色彩變更)，您可以呼叫[GetColor](#getcolor)以取得新的色彩的 RGB 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&52;](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="a-namesetcurrentcolora--ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor  
 呼叫此函式之後呼叫`DoModal`強制在指定的色彩值目前的色彩選擇`clr`。  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
 訊息處理常式中呼叫此函式或`OnColorOK`。 對話方塊會自動更新的值為基礎的使用者選取`clr`參數。  
  
### <a name="example"></a>範例  
  請參閱範例[CColorDialog::OnColorOK](#oncolorok)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../visual-cpp-samples.md)   
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


