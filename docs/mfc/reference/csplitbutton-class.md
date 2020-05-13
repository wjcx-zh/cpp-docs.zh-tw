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
ms.openlocfilehash: 38fceed1cc42ca0aac2e6ddaf145db273c95771d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753126"
---
# <a name="csplitbutton-class"></a>CSplitButton 類別

類`CSplitButton`表示拆分按鈕控件。 當使用者按一下按鈕的主要部分時，分割按鈕控制項會執行預設行為，而當使用者按一下按鈕的下拉箭號時，則顯示下拉式功能表。

## <a name="syntax"></a>語法

```
class CSplitButton : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 拆分按鈕::C 拆分按鈕](#csplitbutton)|建構 `CSplitButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSplit 按鈕:建立](#create)|創建具有指定樣式的拆分按鈕控制項並將其附加到當前`CSplitButton`物件。|
|[CSplit 按鈕::設定下拉選單](#setdropdownmenu)|設置用戶按下目前拆分按鈕控制的下拉箭頭時顯示的下拉選單。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CSplit按鈕:"下拉"](#ondropdown)|處理當用戶按下拉箭頭時系統發送BCN_DROPDOWN通知。|

## <a name="remarks"></a>備註

類`CSplitButton`派生自[CButton](../../mfc/reference/cbutton-class.md)類。 拆分按鈕控件是一個按鈕控件,其樣式為BS_SPLITBUTTON。 當用戶單擊下拉箭頭時,它會顯示自定義功能表。 有關詳細資訊,請參閱[按鈕樣式](/windows/win32/Controls/button-styles)中的BS_SPLITBUTTON和BS_DEFSPLITBUTTON樣式。

下圖描繪了一個對話框,其中包含尋呼機控件和 (1) 拆分按鈕控件。 已按下 (2) 下拉箭頭,並顯示 (3) 子選單。

![包含 Splitbutton 和 Pager 控制項的對話方塊。](../../mfc/reference/media/splitbutton_pager.png "包含 Splitbutton 和 Pager 控制項的對話方塊。")

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

此類在 Windows Vista 和更高版本中受支援。

此類的其他要求在 Windows [Vista 通用控件的生成要求中](../../mfc/build-requirements-for-windows-vista-common-controls.md)介紹。

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplit 按鈕:建立

創建具有指定樣式的拆分按鈕控制項並將其附加到當前`CSplitButton`物件。

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
|*dwStyle*|[在]要應用於控制的樣式的位組合 (OR)。 有關詳細資訊,請參閱[按鍵樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|
|*矩形*|[在]對包含控制項位置和大小的[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用。|
|*pparentwnd*|[在]指向作為控制項的父視窗的[CWnd](../../mfc/reference/cwnd-class.md)物件的非空指標。|
|*nID*|[在]控件的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>C 拆分按鈕::C 拆分按鈕

建構 `CSplitButton` 物件。 建構函數的參數指定一個子功能表,當用戶按一下拆分按鈕控制項的下拉箭頭時顯示該子菜單。

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
|*恩梅努伊*|[在]功能表欄的資源 ID。|
|*nSubMenuId*|[在]子功能表的資源 ID。|
|*pMenu*|[在]指向指定子功能表的[CMenu](../../mfc/reference/cmenu-class.md)物件的指標。 當`CSplitButton`物件超出範圍`CMenu``CSplitButton`時 ,物件將刪除該物件及其關聯的 HMENU。|

### <a name="remarks"></a>備註

使用[CSplitButton::建立](#create)方法創建分割按鈕控制件並將其附加`CSplitButton`到 物件。

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplit按鈕:"下拉"

處理當用戶按下拉箭頭時系統發送BCN_DROPDOWN通知。

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pNMHDR*|[在]指向包含[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知資訊的[NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr)結構的指標。|
|*pResult*|[出](未使用;不返回任何值。[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知的返回值。|

### <a name="remarks"></a>備註

當使用者按下拆分按鈕控制件上的下拉箭頭時,系統會發送BCN_DROPDOWN通知消息,`OnDropDown`該方法將處理該消息。 但是,`CSplitButton`物件不會將BCN_DROPDOWN通知轉發到包含拆分按鈕控件的控制項。 因此,包含控件不支援回應通知的自定義操作。

要實現包含控制項支援的自訂操作,請使用具有BS_SPLITBUTTON樣式的[CButton](../../mfc/reference/cbutton-class.md)物件,`CSplitButton`而不是物件 。 然後在物件中實現BCN_DROPDOWN通知的`CButton`處理程式。 有關詳細資訊,請參閱[按鍵樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

要實現分割按鈕控制項本身支援的自訂操作,請使用[訊息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)。 從`CSplitButton`類派生您自己的類並將其命名,例如,CMySplitButton。 然後向應用程式新增以下訊息對應以處理BCN_DROPDOWN通知:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplit 按鈕::設定下拉選單

設置用戶按下目前拆分按鈕控制的下拉箭頭時顯示的下拉選單。

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*恩梅努伊*|[在]功能表欄的資源 ID。|
|*nSubMenuId*|[在]子功能表的資源 ID。|
|*pMenu*|[在]指向指定子功能表的[CMenu](../../mfc/reference/cmenu-class.md)物件的指標。 當`CSplitButton`物件超出範圍`CMenu``CSplitButton`時 ,物件將刪除該物件及其關聯的 HMENU。|

### <a name="remarks"></a>備註

*nMenuId*參數標識功能表欄,功能表欄是功能表欄項的水準清單。 *nSubMenuId*參數是一個基於零的索引編號,用於標識子功能表,即與每個功能表欄項關聯的功能表項的下拉清單。 例如,典型的應用程式具有包含功能表欄項的功能表,「檔」、「編輯」和「説明」。 "檔案"選單欄項有一個子功能表,其中包含菜單項"打開"、"關閉"和"退出"。 按下拆分按鈕控制件的下拉箭頭時,該控制項將顯示指定的子選單,而不是選單欄。

下圖描繪了一個對話框,其中包含尋呼機控件和 (1) 拆分按鈕控件。 已按下 (2) 下拉箭頭,並顯示 (3) 子選單。

![包含 Splitbutton 和 Pager 控制項的對話方塊。](../../mfc/reference/media/splitbutton_pager.png "包含 Splitbutton 和 Pager 控制項的對話方塊。")

### <a name="example"></a>範例

以下代碼示例中的第一個語句演示了[CSplitButton::SetDropDownMenu](#setdropdownmenu)方法。 我們使用 Visual Studio 資源編輯器創建了功能表,該編輯器自動命名為菜單欄 ID,IDR_MENU1。 *nSubMenuId*參數為零,表示功能表欄的唯一子菜單。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[CSplitButton 類別](../../mfc/reference/csplitbutton-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)
