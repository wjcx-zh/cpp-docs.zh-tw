---
title: CMFCRibbonCustomizePropertyPage 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 57fbd1e1f574beebff8baab014e7ab615f56333f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754169"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 類別

在基於功能區的應用程式中為 **「自定義**」對話框實現自訂頁面。

## <a name="syntax"></a>語法

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFC 功能自定義屬性頁::CMFC 功能定製屬性頁](#cmfcribboncustomizepropertypage)|建構 `CMFCRibbonCustomizePropertyPage` 物件。|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC 功能自訂屬性頁::新增自訂類別](#addcustomcategory)|將自訂類別添加到 **「指令**」組合框。|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC 功能定製屬性頁::OnOK](#onok)|當使用者按下 **「自訂」** 對話方塊上的 **「確定」** 時,系統調用。|

## <a name="remarks"></a>備註

如果要將自定義命令添加到 **「自定義」** 對話方塊中,則必須處理AFX_WM_ON_RIBBON_CUSTOMIZE消息。 在消息處理程式中,實例化堆疊上的`CMFCRibbonCustomizePropertyPage`物件。 建立自定義命令的清單,然後調用`AddCustomCategory`以將新頁面添加到 **「自定義」** 對話方塊中。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCRibbonCustomizePropertyPage`物件和添加自定義類別。

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFC 功能製製屬性頁](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbon自定義對話框.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFC 功能自訂屬性頁::新增自訂類別

將自訂類別添加到 **「指令**」組合框。

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*lpsz名稱*|[在]指定自定義類別名稱。|
|*伊斯蒂迪斯*|[在]包含要在自定義類別中顯示的功能區命令 ID。|

### <a name="remarks"></a>備註

此方法將名為*lpszName 的*類別**加入指令組合**框中。 當使用者選擇該類別時,*在 lstIDS*中指定的命令將顯示在命令清單中。

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFC 功能自定義屬性頁::CMFC 功能定製屬性頁

建構 `CMFCRibbonCustomizePropertyPage` 物件。

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>參數

*pRibbonbar*<br/>
[在]指向要自定義選項的功能區控制件的指標。

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFC 功能定製屬性頁::OnOK

當使用者按下 **「自訂」** 對話方塊上的 **「確定**」時,由系統進行呼叫。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

默認實現將 **「自訂」** 對話方塊選擇的選項應用於「快速存取工具列」。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
