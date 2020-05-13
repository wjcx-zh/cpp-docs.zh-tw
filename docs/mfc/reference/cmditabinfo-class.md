---
title: CMDITabInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 30bf7726b35d762be2bbbd119e0303894879cd3d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752644"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo 類別

該`CMDITabInfo`類用於將參數傳遞給[CMDIFrameWndEx::啟用MDITabbed組](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 設定這個類別的成員以控制 MDI 索引標籤式群組的行為。

## <a name="syntax"></a>語法

```
class CMDITabInfo
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDITab資訊:序列化](#serialize)|從封存中讀取或寫入此物件。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMDITab資訊:m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定「**關閉**」按鈕是否顯示在作用選項卡的標籤上。|
|[CMDITab資訊:m_bAutoColor](#m_bautocolor)|指定是否為 MDI 選項卡著色。|
|[CMDITab資訊:m_bDocumentMenu](#m_bdocumentmenu)|指定選項卡組是顯示顯示打開的文檔列表的彈出功能表還是顯示滾動按鈕。|
|[CMDITab資訊:m_bEnableTabSwap](#m_benabletabswap)|指定使用者是否可以通過拖動交換選項卡的位置。|
|[CMDITab資訊:m_bFlatFrame](#m_bflatframe)|指定選項卡是否具有平面框架。|
|[CMDITab資訊:m_bTabCloseButton](#m_btabclosebutton)|指定每個選項卡標籤是否顯示 **「關閉」** 按鈕。|
|[CMDITab資訊:m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否啟用了自訂工具提示。|
|[CMDITab資訊:m_bTabIcons](#m_btabicons)|指定是否在 MDI 選項卡上顯示圖示。|
|[CMDITab資訊:m_nTabBorderSize](#m_ntabbordersize)|指定每個選項卡視窗的邊框大小。|
|[CMDITab資訊:m_style](#m_style)|指定選項卡標籤的樣式。|
|[CMDITab資訊:m_tabLocation](#m_tablocation)|指定選項卡標籤是位於頁面的頂部還是底部。|

## <a name="remarks"></a>備註

此類指定框架創建的 MDI 選項卡組的參數。

## <a name="example"></a>範例

下面的範例展示如何在類中`CMDITabInfo`設置各種成員變數的值。

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxmdiclient 區域wnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITab資訊:m_bActiveTabCloseButton;

指定「**關閉**」按鈕是否顯示在作用選項卡的標籤上。

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>備註

如果為 TRUE,則活動選項卡的標籤將顯示「**關閉」** 按鈕。 關閉**Close**「按鈕將從選項卡區域的右上角刪除。 否則,活動選項卡的標籤將不會顯示 **"關閉"** 按鈕。 關閉**Close**「按鈕將顯示在選項卡區域的右上角。

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITab資訊:m_bAutoColor

指定每個 MDI 選項卡是否具有自己的顏色。

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>備註

如果為 TRUE,則每個選項卡將有自己的顏色。 顏色集由 MFC 庫管理。 否則,選項卡顯示為白色。 預設值為 FALSE。

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITab資訊:m_bDocumentMenu

指定每個選項卡是否顯示一個彈出功能表,該功能表在選項卡區域的右邊緣顯示打開的文檔清單。

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>備註

如果為 TRUE,則每個選項卡視窗都會顯示一個彈出菜單,該功能表在選項卡區域的右邊緣顯示打開的文檔的清單;如果為 TRUE,則顯示一個彈出視窗。如果為 TRUE,則顯示選項卡區域右側打開的文件清單。否則,選項卡視窗將顯示選項卡區域右邊緣的滾動按鈕。 預設值為 FALSE。

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITab資訊:m_bEnableTabSwap

指定使用者是否可以通過拖動交換選項卡的位置。

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>備註

如果為 TRUE,則使用者可以通過拖動選項卡來更改選項卡位置。 否則,使用者無法更改選項卡位置。 預設值為 TRUE。

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITab資訊:m_bFlatFrame

指定每個選項卡視窗是否具有平面框架。

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITab資訊:m_bTabCloseButton

指定每個選項卡視窗是否顯示 **「關閉」** 按鈕。

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>備註

如果為 TRUE,則每個選項卡視窗都會在選項卡的右邊緣顯示 **「關閉**」按鈕。否則,不顯示 **「關閉**」按鈕。 預設值為 TRUE。

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITab資訊:m_bTabCustomTooltips

指定選項卡是否顯示工具提示。

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>備註

如果為 TRUE,則應用程式向主幀發送AFX_WM_ON_GET_TAB_TOOLTIP消息。 您可以使用ON_REGISTERED_MESSAGE宏來處理此消息。

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITab資訊:m_bTabIcons

指定是否在 MDI 選項卡上顯示圖示。

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>備註

如果為 TRUE,則每個 MDI 選項卡上都會顯示圖示。否則,圖示不會顯示在選項卡上。 預設值為 FALSE。

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITab資訊:m_nTabBorderSize

指定每個選項卡視窗的邊框大小(以像素為單位)。

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>備註

[CMFCVisualManager:getMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)返回預設值。

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITab資訊:m_style

指定選項卡標籤的樣式。

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>備註

指定指定以下樣式之一:

|||
|-|-|
|STYLE_3D|3D 樣式。  |
|STYLE_3D_ONENOTE|微軟 OneNote 樣式。  |
|STYLE_3D_VS2005|微軟視覺工作室2005年風格。  |
|STYLE_3D_SCROLLED|帶矩形選項卡標籤的 3D 樣式。  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|具有共用水準滾動條的平面樣式。  |
|STYLE_3D_ROUNDED_SCROLL|帶圓形標籤的 3D 樣式。  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITab資訊:m_tabLocation

指定選項卡標籤是位於頁面的頂部還是底部。

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>備註

套用於選項卡,以下位置標誌之一:

- LOCATION_BOTTOM:選項卡標籤位於頁面底部。

- LOCATION_TOP:選項卡標籤位於頁面頂部

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITab資訊:序列化

從存檔或存檔讀取或寫入此物件。

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[在]要序列化的[CArchive 類](../../mfc/reference/carchive-class.md)物件。

## <a name="see-also"></a>另請參閱

[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
