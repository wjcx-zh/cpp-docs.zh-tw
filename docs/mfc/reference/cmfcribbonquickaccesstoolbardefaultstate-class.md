---
title: CMFCRibbonQuickAccessToolBarDefaultState 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: eb6b36066f34036ae599a94f4d1c07b2c633e730
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753519"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 類別

管理位於功能區列[(CMFCRibbonBar 類](../../mfc/reference/cmfcribbonbar-class.md))上的快速存取工具列的預設狀態的幫助器類。

## <a name="syntax"></a>語法

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 功能快速存取工具列預設狀態::CMFC 功能快速存取工具列預設狀態](#cmfcribbonquickaccesstoolbardefaultstate)|建構 `CMFCRibbonQuickAccessToolbarDefaultState` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能快速存取工具列預設狀態::新增命令](#addcommand)|將命令添加到快速存取工具列的預設狀態。 這不會改變工具列本身。|
|[CMFC 功能快速存取工具列預設狀態::從](#copyfrom)|將一個快速訪問工具列的屬性複製到另一個工具列。|
|[CMFC 功能快速存取工具列預設狀態::刪除所有](#removeall)|從「快速存取工具列」中刪除所有命令。 這不會改變工具列本身。|

## <a name="remarks"></a>備註

在應用程式中創建快速存取工具列後,我們建議您透過調用[CMFC 功能區列:::設定快速存取預設狀態](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)來設置其預設狀態。 當使用者按一下應用程式 **「選項」** 對話框的 **「自訂**」頁上的 **「重置**」按鈕時,將還原此預設狀態。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFC 功能快速存取工具列預設狀態](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCRibbonQuickAccessToolbarDefaultState`類的物件以及如何將命令添加到快速存取工具列的預設狀態。

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afxribbon 快速存取工具列.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFC 功能快速存取工具列預設狀態::新增命令

將命令添加到快速存取工具列的預設狀態。

```cpp
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>參數

*【在] uiCmd*<br/>
指定命令識別碼。

*[in] bIs 可見*<br/>
設置快速訪問工具列處於默認狀態時命令的可見性。

### <a name="remarks"></a>備註

向 CMFC 功能刪除快速存取工具預設狀態添加命令可完成三個結果。 首先,每個添加的命令都列在快速訪問工具列右側的下拉清單中。 通過這種方式,用戶可以輕鬆地從「快速存取」工具列中添加或刪除該命令。 其次,將重置「快速存取工具列」,以僅顯示當使用者按**一下「自訂」** 對話方塊中的 **「重置**」按鈕時,在預設狀態下列為可見的命令。 第三,如果您沒有調用[CMFCRibbonBar::SetQuickAccess命令](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands),則快速存取工具列使用此清單中的可見命令作為使用者首次運行應用程式的預設可見命令。 添加所需的所有命令后,請致電[CMFCRibbonBar::設定快速存取預設狀態](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate),以將此實例設置為該功能區列的快速存取工具列的默認狀態。

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFC 功能快速存取工具列預設狀態::從

將一個快速訪問工具列的屬性複製到另一個工具列。

```cpp
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]對要從中複製`CMFCRibbonQuickAccessToolBarDefaultState`的源物件的引用。

### <a name="remarks"></a>備註

此方法使用`CMFCRibbonQuickAccessToolBarDefaultState`[CMFCRibbonQuickAccessToolBarDefaultState:addCommand](#addcommand)方法將每個命令從源物件複製到此物件。

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFC 功能快速存取工具列預設狀態::CMFC 功能快速存取工具列預設狀態

建構快速存取工具列預設狀態物件。

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>備註

默認情況下[,CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)的新實例包含的命令清單為空。

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFC 功能快速存取工具列預設狀態::刪除所有

清除「快速存取工具列」中的預設命令清單。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

此函數從此實例中刪除以前調用[CMFC 功能障礙快速存取工具列預設狀態的所有命令:添加 AddCommand。](#addcommand)

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
