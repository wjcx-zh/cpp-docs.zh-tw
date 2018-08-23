---
title: CSplitButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
dev_langs:
- C++
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7fd35c351639d4b7b5f3b9dbbbce1c5e7cbcb79
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538821"
---
# <a name="csplitbutton-class"></a>CSplitButton 類別
`CSplitButton`類別代表分割按鈕控制項。 當使用者按一下按鈕的主要部分時，分割按鈕控制項會執行預設行為，而當使用者按一下按鈕的下拉箭號時，則顯示下拉式功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|建構 `CSplitButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|使用指定的樣式中建立分割按鈕控制項，並將它附加至目前`CSplitButton`物件。|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|設定當使用者按一下目前的分割按鈕控制項的下拉箭號會顯示下拉式選單。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|處理當使用者按一下目前的分割按鈕控制項的下拉箭號時，系統會傳送 BCN_DROPDOWN 通知。|  
  
## <a name="remarks"></a>備註  
 `CSplitButton`類別衍生自[CButton](../../mfc/reference/cbutton-class.md)類別。 分割按鈕控制項是其樣式為 BS_SPLITBUTTON 按鈕控制項。 當使用者按一下下拉箭號，它就會顯示一個自訂功能表。 如需詳細資訊，請參閱 BS_SPLITBUTTON BS_DEFSPLITBUTTON 中的和樣式[按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)。  
  
 下圖說明對話方塊中，其中包含頁面巡覽區控制項和 (1) 的分割按鈕控制項。 已按下的 (2) 的下拉式箭號，並顯示 (3) 的子功能表。  
  
 ![包含 splitbutton 和 pager 控制項對話方塊。](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
 這個類別支援在 Windows Vista 和更新版本。  
  
 這個類別的其他需求所述[建置需求的 Windows Vista 通用控制項](../../mfc/build-requirements-for-windows-vista-common-controls.md)。  
  
##  <a name="create"></a>  CSplitButton::Create  
 使用指定的樣式中建立分割按鈕控制項，並將它附加至目前`CSplitButton`物件。  
  
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
|[in]*cheaderctrl:: Create*|位元組合 (OR) 套用至控制項的樣式。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|  
|[in]*rect*|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，包含控制項的大小與位置。|  
|[in]*pParentWnd*|非 null 指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。|  
|[in]*nID*|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton  
 建構 `CSplitButton` 物件。 建構函式的參數會指定當使用者按一下分割按鈕控制項的下拉式箭號會顯示子功能表。  
  
```  
CSplitButton();

 
CSplitButton(
    UINT nMenuId,   
    UINT nSubMenuId)  
CSplitButton(CMenu* pMenu)  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*nMenuId*|在功能表列的資源識別碼。|  
|[in]*nSubMenuId*|為子功能表的資源識別碼。|  
|[in]*pMenu*|指標[CMenu](../../mfc/reference/cmenu-class.md)物件，指定子功能表。 `CSplitButton`物件刪除`CMenu`物件和其相關聯的 HMENU 時`CSplitButton`物件超出範圍。|  
  
### <a name="remarks"></a>備註  
 使用[CSplitButton::Create](#create)方法來建立分割按鈕控制項，並將其附加至`CSplitButton`物件。  
  
##  <a name="ondropdown"></a>  CSplitButton::OnDropDown  
 處理當使用者按一下目前的分割按鈕控制項的下拉箭號時，系統會傳送 BCN_DROPDOWN 通知。  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*pNMHDR*|指標[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)結構，其中包含有關的資訊[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
|[out]*pResult*|（未使用，會傳回任何值）。傳回值[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
  
### <a name="remarks"></a>備註  
 當使用者按一下下拉箭號，分割按鈕控制項上的時，系統會傳送 BCN_DROPDOWN 通知訊息，其中`OnDropDown`方法控制代碼。 不過，`CSplitButton`物件不會轉送 BCN_DROPDOWN 通知，以包含分割按鈕控制項的控制項。 因此，包含控制項無法支援的自訂動作以回應通知。  
  
 若要實作的自訂動作，包含控制項支援，請使用[CButton](../../mfc/reference/cbutton-class.md)物件而不是 BS_SPLITBUTTON 樣式`CSplitButton`物件。 然後實作 BCN_DROPDOWN 通知中的處理常式`CButton`物件。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。  
  
 若要實作自訂動作，分割按鈕控制項本身支援，請使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)。 衍生您自己的類別，從`CSplitButton`類別，並加以命名，例如 CMySplitButton。 然後新增下列的訊息對應至您的應用程式，以處理 BCN_DROPDOWN 通知：  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu  
 設定當使用者按一下目前的分割按鈕控制項的下拉箭號會顯示下拉式選單。  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*nMenuId*|在功能表列的資源識別碼。|  
|[in]*nSubMenuId*|為子功能表的資源識別碼。|  
|[in]*pMenu*|指標[CMenu](../../mfc/reference/cmenu-class.md)物件，指定子功能表。 `CSplitButton`物件刪除`CMenu`物件和其相關聯的 HMENU 時`CSplitButton`物件超出範圍。|  
  
### <a name="remarks"></a>備註  
 *NMenuId*參數會識別功能表列，也就是水平功能表列項目清單。 *NSubMenuId*參數是以零為起始的索引編號識別的子功能表，也就是下拉式清單中的每個功能表列項目相關聯的功能表項目。 比方說，一般的應用程式有一個包含功能表的功能表列項目，「 檔案 」，[編輯] 和 [說明]。 [檔案] 功能表列項目具有子功能表，其中包含的功能表項目中，[開啟，]"Close"和"Exit"。 按一下下拉箭號，分割按鈕控制項時，控制項就會顯示指定的子功能表功能表列。  
  
 下圖說明對話方塊中，其中包含頁面巡覽區控制項和 (1) 的分割按鈕控制項。 已按下的 (2) 的下拉式箭號，並顯示 (3) 的子功能表。  
  
 ![包含 splitbutton 和 pager 控制項對話方塊。](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>範例  
 第一個陳述式，在下列程式碼範例示範[CSplitButton::SetDropDownMenu](#setdropdownmenu)方法。 我們建立功能表與 Visual Studio 資源編輯器，它會自動命名為功能表列的識別碼，IDR_MENU1。 *NSubMenuId*參數，也就是零，指的是唯一的子功能表中的功能表列。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CSplitButton 類別](../../mfc/reference/csplitbutton-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)
