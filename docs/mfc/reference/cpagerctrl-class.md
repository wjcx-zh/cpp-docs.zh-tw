---
title: "CPagerCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c79fa877023c7a01c4814f61d75a54cb0dd64b51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cpagerctrl-class"></a>CPagerCtrl 類別
`CPagerCtrl` 類別會封裝 Windows 頁面巡覽區控制項，可以將不符合容器視窗大小的包含視窗捲動到檢視中。  
  
## <a name="syntax"></a>語法  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|建構 `CPagerCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|使用指定的樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。|  
|[CPagerCtrl::CreateEx](#createex)|使用指定的延伸樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|啟用或停用轉送[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)到包含在目前的頁面巡覽區控制項的視窗訊息。|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|擷取目前的頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::GetBorder](#getborder)|擷取目前的頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|擷取目前的頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|擷取目前的頁面巡覽區控制項中指定的按鍵的狀態。|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)目前的頁面巡覽區控制項的介面。|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|擷取目前的頁面巡覽區控制項的捲動位置。|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|指出目前的頁面巡覽區控制項的指定的按鈕處於`pressed`狀態。|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|指出目前的頁面巡覽區控制項的指定的按鈕處於`grayed`狀態。|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|指出目前的頁面巡覽區控制項的指定的按鈕處於`hot`狀態。|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|指出目前的頁面巡覽區控制項的指定的按鈕處於`invisible`狀態。|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|指出目前的頁面巡覽區控制項的指定的按鈕處於`normal`狀態。|  
|[CPagerCtrl::RecalcSize](#recalcsize)|導致目前的頁面巡覽區控制項重新計算包含視窗的大小。|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|設定目前的頁面巡覽區控制項的背景色彩。|  
|[CPagerCtrl::SetBorder](#setborder)|設定目前的頁面巡覽區控制項的框線大小。|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|設定目前的頁面巡覽區控制項的按鈕大小。|  
|[CPagerCtrl::SetChild](#setchild)|設定目前的頁面巡覽區控制項的包含的視窗。|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|設定目前的頁面巡覽區控制項的捲動位置。|  
  
## <a name="remarks"></a>備註  
 頁面巡覽區控制項是包含線性和大於所包含的視窗，並可讓您包含的視窗捲動到檢視的另一個視窗的視窗。 頁面巡覽區控制項顯示兩個捲軸按鈕，會自動地消失包含的視窗捲動至最遠的範圍，與否則會再度出現。 您可以建立水平或垂直捲動頁面巡覽區控制項。  
  
 比方說，如果您的應用程式工具列的寬度不足以顯示所有的項目，將頁面巡覽區控制項的工具列，使用者將能夠捲動工具列的左邊或右邊，存取所有項目。 Microsoft Internet Explorer 版本 4.0 （commctrl.dll 版本 4.71） 導入了頁面巡覽區控制項。  
  
 `CPagerCtrl`類別衍生自[CWnd](../../mfc/reference/cwnd-class.md)類別。 如需詳細資訊和頁面巡覽區控制項的說明，請參閱[呼叫器控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl  
 建構 `CPagerCtrl` 物件。  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>備註  
 使用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)方法來建立頁面巡覽區控制項，並將其附加至`CPagerCtrl`物件。  
  
##  <a name="create"></a>CPagerCtrl::Create  
 使用指定的樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `dwStyle`|位元組合 (OR)[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)来套用至控制項。|  
|[輸入] `rect`|若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含用戶端座標中控制項的大小與位置。|  
|[輸入] `pParentWnd`|指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 此參數不得為`NULL`。|  
|[輸入] `nID`|控制項的識別碼。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 若要建立頁面巡覽區控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)上該變數的方法。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，然後使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素框線粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CPagerCtrl::CreateEx  
 使用指定的延伸樣式建立頁面巡覽區控制項，並將其附加至目前`CPagerCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `dwExStyle`|若要套用至控制項的延伸樣式的位元組合。 如需詳細資訊，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式。|  
|[輸入] `dwStyle`|位元組合 (OR)[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)来套用至控制項。|  
|[輸入] `rect`|若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含用戶端座標中控制項的大小與位置。|  
|[輸入] `pParentWnd`|指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 此參數不得為`NULL`。|  
|[輸入] `nID`|控制項的識別碼。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 若要建立頁面巡覽區控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)上該變數的方法。  
  
##  <a name="forwardmouse"></a>CPagerCtrl::ForwardMouse  
 啟用或停用轉送[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)到包含在目前的頁面巡覽區控制項的視窗訊息。  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `bForward`|`true`將滑鼠訊息轉送或`false`不將滑鼠訊息轉送。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867) Windows SDK 中所述的訊息。  
  
##  <a name="getborder"></a>CPagerCtrl::GetBorder  
 擷取目前的頁面巡覽區控制項的框線大小。  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的框線大小，以像素表示。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::GetBorder](#getborder)方法來擷取頁面巡覽區控制項的邊框的粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>CPagerCtrl::GetBkColor  
 擷取目前的頁面巡覽區控制項的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，包含目前的頁面巡覽區控制項的背景顏色。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法，以設定頁面巡覽區控制項的背景色彩為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法以確認已進行變更。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize  
 擷取目前的頁面巡覽區控制項的按鈕大小。  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的按鈕大小，以像素表示。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870) Windows SDK 中所述的訊息。  
  
 如果頁面巡覽區控制項的`PGS_HORZ`樣式，按鈕的大小決定頁面巡覽區按鈕的寬度與頁面巡覽區控制項有`PGS_VERT`樣式，按鈕的大小會決定頁面巡覽區按鈕的高度。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
##  <a name="getbuttonstate"></a>CPagerCtrl::GetButtonState  
 擷取目前的頁面巡覽區控制項中指定的捲動按鈕的狀態。  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 所指定按鈕的狀態`iButton`參數。 狀態為`PGF_INVISIBLE`， `PGF_NORMAL`， `PGF_GRAYED`， `PGF_DEPRESSED`，或`PGF_HOT`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。  
  
##  <a name="getdroptarget"></a>CPagerCtrl::GetDropTarget  
 擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)目前的頁面巡覽區控制項的介面。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDropTarget`目前的頁面巡覽區控制項的介面。  
  
### <a name="remarks"></a>備註  
 `IDropTarget`是您所實作的介面的其中一個應用程式中支援拖放作業。  
  
 這個方法會傳送[PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872) Windows SDK 中所述的訊息。 這個方法的呼叫端會負責呼叫`Release`隸屬[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)介面時不再需要的介面。  
  
##  <a name="getscrollpos"></a>CPagerCtrl::GetScrollPos  
 擷取目前的頁面巡覽區控制項的捲動位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的捲動位置，以像素表示。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::GetScrollPos](#getscrollpos)方法來擷取目前的頁面巡覽區控制項的捲動位置。 如果為零，最左邊的位置，已經不捲動頁面巡覽區控制項的範例會使用[CPagerCtrl::SetScrollPos](#setscrollpos)方法，以將捲軸位置設定為零。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed  
 指出目前的頁面巡覽區控制項的指定捲軸按鈕是否按下狀態。  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕是處於按下狀態;否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。 然後它會測試是否會傳回的狀態為`PGF_DEPRESSED`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed  
 指出目前的頁面巡覽區控制項的指定捲軸按鈕是否呈現灰色的狀態。  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕在呈現灰色的狀態;否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。 然後它會測試是否會傳回的狀態為`PGF_GRAYED`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot  
 指出目前的頁面巡覽區控制項的指定捲軸按鈕處於作用中狀態。  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕處於作用中狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。 然後它會測試是否會傳回的狀態為`PGF_HOT`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible  
 指出目前的頁面巡覽區控制項的指定捲軸按鈕是否可見狀態。  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕處於隱藏狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 Windows 讓捲軸按鈕中的特定方向不可見時因為按一下按鈕進一步無法讓多個包含視窗檢視包含的視窗捲動到其最遠的範圍。  
  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。 然後它會測試是否會傳回的狀態為`PGF_INVISIBLE`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)方法，以判斷是否頁面巡覽區控制項的左和向右捲動按鈕會顯示。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal  
 指出目前的頁面巡覽區控制項的指定捲軸按鈕處於正常狀態。  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButton`|表示要擷取狀態的按鈕。 如果頁面巡覽區控制項樣式`PGS_HORZ`，指定`PGB_TOPORLEFT`左邊的按鈕和`PGB_BOTTOMORRIGHT`右邊的按鈕。 如果頁面巡覽區控制項樣式`PGS_VERT`，指定`PGB_TOPORLEFT`頂端的按鈕和`PGB_BOTTOMORRIGHT`底部的按鈕。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的按鈕處於正常狀態。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) Windows SDK 中所述的訊息。 然後它會測試是否會傳回的狀態為`PGF_NORMAL`。 如需詳細資訊，請參閱 > 一節會傳回值[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)訊息。  
  
##  <a name="recalcsize"></a>CPagerCtrl::RecalcSize  
 導致目前的頁面巡覽區控制項重新計算包含視窗的大小。  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876) Windows SDK 中所述的訊息。 因此，呼叫器控制項傳送[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知，以取得包含視窗的可捲動的維度。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::RecalcSize](#recalcsize)方法來要求重新計算其大小目前的頁面巡覽區控制項。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>範例  
 下列範例會使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)啟用重新計算並不需要執行之計算的控制項的父對話方塊大小的頁面巡覽區控制項。 此範例衍生`MyPagerCtrl`類別從[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)，然後使用相關聯的訊息對應[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知`OnCalcsize`通知處理常式。 此範例中，通知處理常式設定頁面巡覽區控制項的高度與寬度為固定值。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>CPagerCtrl::SetBkColor  
 設定目前的頁面巡覽區控制項的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `clrBk`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，包含新的頁面巡覽區控制項的背景色彩。|  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，包含前一個頁面巡覽區控制項的背景色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法，以設定頁面巡覽區控制項的背景色彩為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法以確認已進行變更。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>CPagerCtrl::SetBorder  
 設定目前的頁面巡覽區控制項的框線大小。  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iBorder`|新的框線大小，以像素表示。 如果`iBorder`參數是負數，框線大小設為零。|  
  
### <a name="return-value"></a>傳回值  
 先前的框線大小，以像素表示。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，然後使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素框線粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize  
 設定目前的頁面巡覽區控制項的按鈕大小。  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iButtonSize`|新按鈕的大小，以像素表示。|  
  
### <a name="return-value"></a>傳回值  
 先前的按鈕大小，以像素表示。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886) Windows SDK 中所述的訊息。  
  
 如果頁面巡覽區控制項的`PGS_HORZ`樣式，按鈕的大小決定頁面巡覽區按鈕的寬度與頁面巡覽區控制項有`PGS_VERT`樣式，按鈕的大小會決定頁面巡覽區按鈕的高度。 預設按鈕的大小是四分之三的捲軸的寬度，而最小的按鈕大小為 12 個像素。 如需詳細資訊，請參閱[呼叫器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，然後使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素框線粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>CPagerCtrl::SetChild  
 設定目前的頁面巡覽區控制項的包含的視窗。  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `hwndChild`|包含視窗的控制代碼。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884) Windows SDK 中所述的訊息。  
  
 這個方法不會變更父系的包含視窗;它只會指派給捲動頁面巡覽區控制項的視窗控制代碼。 在大部分情況下，包含的視窗將頁面巡覽區控制項的子視窗。  
  
### <a name="example"></a>範例  
 下列範例會建立頁面巡覽區控制項，然後使用[CPagerCtrl::SetChild](#setchild)方法與頁面巡覽區控制項很長的按鈕控制項。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽區控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素框線粗細。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setscrollpos"></a>CPagerCtrl::SetScrollPos  
 設定目前的頁面巡覽區控制項的捲動位置。  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `iPos`|新的捲動位置，以像素表示。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886) Windows SDK 中所述的訊息。  
  
## <a name="see-also"></a>請參閱  
 [CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [頁面巡覽區控制項](http://msdn.microsoft.com/library/windows/desktop/bb760855)



