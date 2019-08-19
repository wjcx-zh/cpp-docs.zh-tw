---
title: CSplitButton 類別
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: a552334adb4963f45388a798eb0723e61c09ec85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502844"
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
|[CSplitButton::Create](#create)|建立具有指定樣式的分割按鈕控制項, 並將它附加至`CSplitButton`目前的物件。|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|設定當使用者按一下目前分割按鈕控制項的下拉箭號時, 所顯示的下拉式功能表。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|處理當使用者按一下目前分割按鈕控制項的下拉箭號時, 系統所傳送的 BCN_DROPDOWN 通知。|

## <a name="remarks"></a>備註

類別衍生自 [CButton](../../mfc/reference/cbutton-class.md) 類別。`CSplitButton` 分割按鈕控制項是其樣式為 BS_SPLITBUTTON 的按鈕控制項。 當使用者按一下下拉箭號時, 它會顯示自訂功能表。 如需詳細資訊, 請參閱[按鈕樣式](/windows/win32/Controls/button-styles)中的 BS_SPLITBUTTON 和 BS_DEFSPLITBUTTON 樣式。

下圖說明一個對話方塊, 其中包含一個分頁控制項和一個 (1) 分割按鈕控制項。 已按下 (2) 下拉箭號, 並顯示 (3) 子功能表。

![具有 splitbutton 和呼機控制項的對話方塊。](../../mfc/reference/media/splitbutton_pager.png "具有 splitbutton 和呼機控制項的對話方塊。")

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

Windows Vista 和更新版本支援此類別。

如需此類別的其他需求, 請參閱[Windows Vista 通用控制項的組建需求](../../mfc/build-requirements-for-windows-vista-common-controls.md)。

##  <a name="create"></a>  CSplitButton::Create

建立具有指定樣式的分割按鈕控制項, 並將它附加至`CSplitButton`目前的物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*dwStyle*|在要套用至控制項之樣式的位元組合 (OR)。 如需詳細資訊, 請參閱[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|
|*rect*|在[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 其中包含控制項的位置和大小。|
|*pParentWnd*|在[CWnd](../../mfc/reference/cwnd-class.md)物件的非 null 指標, 這是控制項的父視窗。|
|*nID*|在控制項的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

##  <a name="csplitbutton"></a>CSplitButton:: CSplitButton

建構 `CSplitButton` 物件。 此函式的參數會指定當使用者按一下 [分割按鈕] 控制項的下拉箭號時, 所顯示的子功能表。

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
|*nMenuId*|在功能表列的資源識別碼。|
|*nSubMenuId*|在子功能表的資源識別碼。|
|*pMenu*|在指定子功能表之[CMenu](../../mfc/reference/cmenu-class.md)物件的指標。 當物件超出範圍`CMenu`時`CSplitButton` `CSplitButton` , 物件會刪除物件及其相關聯的 HMENU。|

### <a name="remarks"></a>備註

使用[CSplitButton:: create](#create)方法來建立分割按鈕控制項, 並將它附加至`CSplitButton`物件。

##  <a name="ondropdown"></a>CSplitButton:: OnDropDown

處理當使用者按一下目前分割按鈕控制項的下拉箭號時, 系統所傳送的 BCN_DROPDOWN 通知。

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pNMHDR*|在[NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr)結構的指標, 其中包含[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知的相關資訊。|
|*pResult*|脫銷(未使用; 不會傳回任何值)。[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知的傳回值。|

### <a name="remarks"></a>備註

當使用者按一下分割按鈕控制項上的下拉箭號時, 系統就`OnDropDown`會傳送 BCN_DROPDOWN 通知訊息, 方法會處理此訊息。 不過, `CSplitButton`物件不會將 BCN_DROPDOWN 通知轉送至包含分割按鈕控制項的控制項。 因此, 包含控制項無法支援自訂動作來回應通知。

若要執行包含控制項支援的自訂動作, 請使用[CButton](../../mfc/reference/cbutton-class.md)物件搭配 BS_SPLITBUTTON 樣式, 而不`CSplitButton`是物件。 然後在`CButton`物件中, 為 BCN_DROPDOWN 通知執行處理常式。 如需詳細資訊, 請參閱[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

若要執行分割按鈕控制項本身支援的自訂動作, 請使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)。 從類別衍生您自己的`CSplitButton`類別, 並將其命名為, 例如 CMySplitButton。 然後將下列訊息對應新增至您的應用程式, 以處理 BCN_DROPDOWN 通知:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>CSplitButton:: SetDropDownMenu

設定當使用者按一下目前分割按鈕控制項的下拉箭號時, 所顯示的下拉式功能表。

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*nMenuId*|在功能表列的資源識別碼。|
|*nSubMenuId*|在子功能表的資源識別碼。|
|*pMenu*|在指定子功能表之[CMenu](../../mfc/reference/cmenu-class.md)物件的指標。 當物件超出範圍`CMenu`時`CSplitButton` `CSplitButton` , 物件會刪除物件及其相關聯的 HMENU。|

### <a name="remarks"></a>備註

*NMenuId*參數會識別功能表列, 這是功能表列專案的水準清單。 *NSubMenuId*參數是以零為基底的索引編號, 用來識別子功能表, 這是與每個功能表列專案相關聯之功能表項目的下拉式清單。 例如, 一般應用程式有一個功能表, 其中包含功能表列專案、[檔案]、[編輯] 和 [說明]。 [檔案] 功能表列專案有一個子功能表, 其中包含功能表項目 [開啟]、[關閉] 和 [結束]。 按一下分割按鈕控制項的下拉箭號時, 控制項會顯示指定的子功能表, 而不是功能表列。

下圖說明一個對話方塊, 其中包含一個分頁控制項和一個 (1) 分割按鈕控制項。 已按下 (2) 下拉箭號, 並顯示 (3) 子功能表。

![具有 splitbutton 和呼機控制項的對話方塊。](../../mfc/reference/media/splitbutton_pager.png "具有 splitbutton 和呼機控制項的對話方塊。")

### <a name="example"></a>範例

下列程式碼範例中的第一個語句示範[CSplitButton:: SetDropDownMenu](#setdropdownmenu)方法。 我們建立了具有 Visual Studio 資源編輯器的功能表, 其會自動命名為 IDR_MENU1 的功能表列識別碼。 *NSubMenuId*參數為零, 表示功能表列的唯一子功能表。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[CSplitButton 類別](../../mfc/reference/csplitbutton-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)
