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
ms.openlocfilehash: 92408e91b41b474da3a2da6ad0646feb3a6b8fc2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831836"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 類別

在功能區應用程式中，為 [ **自訂** ] 對話方塊執行自訂頁面。

## <a name="syntax"></a>語法

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|建構 `CMFCRibbonCustomizePropertyPage` 物件。|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|將自訂分類加入至 [ **命令** ] 下拉式方塊。|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|
|[CMFCRibbonCustomizePropertyPage：： OnOK](#onok)|當使用者在 [**自訂**] 對話方塊中按一下 **[確定]** 時由系統呼叫。|

## <a name="remarks"></a>備註

如果您想要將自訂命令新增至 [ **自訂** ] 對話方塊，您必須處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息。 在訊息處理常式中，具現化 `CMFCRibbonCustomizePropertyPage` 堆疊上的物件。 建立自訂命令清單，然後呼叫 `AddCustomCategory` 以將新頁面新增至 [ **自訂** ] 對話方塊。

## <a name="example"></a>範例

下列範例示範如何建立 `CMFCRibbonCustomizePropertyPage` 物件以及加入自訂分類。

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxribboncustomizedialog。h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a> CMFCRibbonCustomizePropertyPage::AddCustomCategory

將自訂分類加入至 [ **命令** ] 下拉式方塊。

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>參數

*lpszName*\
在指定自訂分類名稱。

*lstIDS*\
在包含要顯示在自訂分類中的功能區命令識別碼。

### <a name="remarks"></a>備註

這個方法會將名為 *lpszName* 的類別加入至 [ **命令** ] 下拉式方塊。 當使用者選取類別時，[ *lstIDS* ] 中指定的命令會出現在命令清單中。

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a> CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

建構 `CMFCRibbonCustomizePropertyPage` 物件。

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>參數

*pRibbonBar*<br/>
在功能區控制項的指標，可供自訂的選項。

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a> CMFCRibbonCustomizePropertyPage：： OnOK

當使用者在 [**自訂**] 對話方塊中按一下 **[確定]** 時，由系統 Calleld。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

預設的執行會將 [ **自訂** ] 對話方塊中選取的選項套用至快速存取工具列。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
