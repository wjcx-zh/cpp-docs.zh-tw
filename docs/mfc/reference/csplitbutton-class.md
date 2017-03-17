---
title: "CSplitButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CSplitButton class
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
caps.latest.revision: 24
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
ms.openlocfilehash: b4c038a177d5c501d4baad8eaa208af0e76ce231
ms.lasthandoff: 02/24/2017

---
# <a name="csplitbutton-class"></a>CSplitButton 類別
`CSplitButton`類別代表分割按鈕控制項。 當使用者按一下按鈕的主要部分時，分割按鈕控制項會執行預設行為，而當使用者按一下按鈕的下拉箭號時，則顯示下拉式功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|建構 `CSplitButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|使用指定的樣式建立分割按鈕控制項，並將其附加至目前`CSplitButton`物件。|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|設定當使用者按一下目前的分割按鈕控制項的下拉式箭號會顯示下拉式選單。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|處理`BCN_DROPDOWN`使用者按下的下拉式箭號，目前的分割按鈕控制項時，系統會傳送的通知。|  
  
## <a name="remarks"></a>備註  
 `CSplitButton`類別衍生自[CButton](../../mfc/reference/cbutton-class.md)類別。 分割按鈕控制項是按鈕控制項的樣式是`BS_SPLITBUTTON`。 當使用者按一下下拉箭號，它會顯示自訂功能表。 如需詳細資訊，請參閱`BS_SPLITBUTTON`和`BS_DEFSPLITBUTTON`樣式中[按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)。  
  
 下圖說明對話方塊，其中包含頁面巡覽區控制項和 (1) 的分割按鈕控制項。 已按下 (2) 的下拉箭號，並顯示 [(3)] 子功能表。  
  
 ![包含 splitbutton 和 pager 控制項的對話方塊。] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
 這個類別支援[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]和更新版本。  
  
 這個類別的其他需求所述[建置需求的 Windows Vista 通用控制項](../../mfc/build-requirements-for-windows-vista-common-controls.md)。  
  
##  <a name="create"></a>CSplitButton::Create  
 使用指定的樣式建立分割按鈕控制項，並將其附加至目前`CSplitButton`物件。  
  
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
|[in] `dwStyle`|位元組合 (OR) 的樣式套用至控制項。 如需詳細資訊，請參閱[按鈕樣式](../../mfc/reference/button-styles.md)。|  
|[in] `rect`|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，包含控制項的大小與位置。|  
|[in] `pParentWnd`|非 null 指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。|  
|[in] `nID`|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
##  <a name="csplitbutton"></a>CSplitButton::CSplitButton  
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
|[in] `nMenuId`|在功能表列的資源識別碼。|  
|[in] `nSubMenuId`|子功能表資源識別碼。|  
|[in] `pMenu`|指標[CMenu](../../mfc/reference/cmenu-class.md)物件，指定子功能表。 `CSplitButton`物件刪除`CMenu`物件和其相關聯`HMENU`時`CSplitButton`物件超出範圍。|  
  
### <a name="remarks"></a>備註  
 使用[CSplitButton::Create](#create)方法來建立分割按鈕控制項，並將其附加至`CSplitButton`物件。  
  
##  <a name="ondropdown"></a>CSplitButton::OnDropDown  
 處理`BCN_DROPDOWN`使用者按下的下拉式箭號，目前的分割按鈕控制項時，系統會傳送的通知。  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pNMHDR`|指標[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)包含的相關資訊的結構[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
|[輸出] `pResult`|（不使用，會傳回任何值）。傳回值的[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
  
### <a name="remarks"></a>備註  
 當使用者按一下下拉箭號，分割按鈕控制項上的時，系統會傳送`BCN_DROPDOWN`通知訊息，其中`OnDropDown`方法會處理。 不過，`CSplitButton`物件不會轉送`BCN_DROPDOWN`包含分割按鈕控制項的控制項的通知。 因此，包含控制項無法支援的自訂動作以回應的通知。  
  
 若要實作的自訂動作，包含控制項的支援，請使用[CButton](../../mfc/reference/cbutton-class.md)物件使用樣式的`BS_SPLITBUTTON`而不是`CSplitButton`物件。 然後實作的處理常式`BCN_DROPDOWN`中的通知`CButton`物件。 如需詳細資訊，請參閱[按鈕樣式](../../mfc/reference/button-styles.md)。  
  
 若要實作自訂動作，分割按鈕控制項本身支援，請使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)。 衍生您自己從`CSplitButton`類別，並加以命名，例如 CMySplitButton。 然後將下列的訊息對應新增至應用程式以處理`BCN_DROPDOWN`通知︰  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu  
 設定當使用者按一下目前的分割按鈕控制項的下拉式箭號會顯示下拉式選單。  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nMenuId`|在功能表列的資源識別碼。|  
|[in] `nSubMenuId`|子功能表資源識別碼。|  
|[in] `pMenu`|指標[CMenu](../../mfc/reference/cmenu-class.md)物件，指定子功能表。 `CSplitButton`物件刪除`CMenu`物件和其相關聯`HMENU`時`CSplitButton`物件超出範圍。|  
  
### <a name="remarks"></a>備註  
 `nMenuId`參數識別的功能表列，也就是水平功能表列項目清單。 `nSubMenuId`參數是以零為起始的索引編號來識別子功能表，這是每個功能表列項目相關聯的功能表項目的下拉式清單。 例如，一般應用程式有一個包含功能表的功能表列項目，「 檔案 」，「 編輯 」 和 「 支援 」。 [檔案] 功能表列項目具有子功能表，其中包含的功能表項目中，「 開啟，」 「 關閉 」 和 「 結束 」。 按一下下拉式箭號，分割按鈕控制項時，控制項就會顯示指定的子功能表，功能表列。  
  
 下圖說明對話方塊，其中包含頁面巡覽區控制項和 (1) 的分割按鈕控制項。 已按下 (2) 的下拉箭號，並顯示 [(3)] 子功能表。  
  
 ![包含 splitbutton 和 pager 控制項的對話方塊。] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>範例  
 下列程式碼範例中的第一個陳述式示範[CSplitButton::SetDropDownMenu](#setdropdownmenu)方法。 我們建立功能表與 Visual Studio 資源編輯器，自動命名的功能表列的識別碼， `IDR_MENU1`。 `nSubMenuId`參數，也就是零，指的是唯一的子功能表的功能表列。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CSplitButton 類別](../../mfc/reference/csplitbutton-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)

