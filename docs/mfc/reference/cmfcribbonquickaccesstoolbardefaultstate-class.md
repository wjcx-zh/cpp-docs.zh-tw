---
title: CMFCRibbonQuickAccessToolBarDefaultState 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7e237d5c1c7eb1eda792c6cbbc028960d851c07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380356"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 類別

為您管理預設狀態的快速存取工具列位於功能區列的 helper 類別 ( [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md))。

## <a name="syntax"></a>語法

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|建構 `CMFCRibbonQuickAccessToolbarDefaultState` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|將命令加入至預設狀態中，快速存取工具列。 這不會變更工具列本身。|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|一個快速存取工具列屬性複製到另一個。|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|移除 快速存取工具列中的所有命令。 這不會變更工具列本身。|

## <a name="remarks"></a>備註

您將快速存取工具列在您的應用程式之後，我們建議您設定其預設狀態，藉由呼叫[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)。 這個預設狀態還原時使用者按下**重設**按鈕**自訂**應用程式頁面**選項** 對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCRibbonQuickAccessToolbarDefaultState`類別，以及如何將命令加入至預設狀態中，快速存取工具列。

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

將命令加入至預設狀態中，快速存取工具列。

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>參數

*[] in uiCmd*<br/>
指定命令識別碼。

*[] in bIsVisible*<br/>
快速存取工具列中的預設狀態時，請設定命令的可見性。

### <a name="remarks"></a>備註

將命令加入至 CMFCRibbonQuickAccessToolBarDefaultState 完成三個結果。 首先，新增的每個命令會列在 快速存取工具列右邊的下拉式清單中。 以這種方式，使用者可以輕鬆地新增或移除快速存取工具列中的該命令。 第二，快速存取工具列會重設為只顯示這些命令列出為可見的預設狀態中當使用者按一下**重設**按鈕**自訂** 對話方塊。 第三，如果您未呼叫[CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)，快速存取工具列使用從這份清單的可見命令的預設顯示的命令的使用者執行您的應用程式的第一次。 您已新增您想要的所有命令之後，請呼叫[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)来設定該功能區列的 快速存取工具列預設狀態為這個執行個體。

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

一個快速存取工具列屬性複製到另一個。

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]來源的參考`CMFCRibbonQuickAccessToolBarDefaultState`從複製的物件。

### <a name="remarks"></a>備註

這個方法會從來源複製每個命令`CMFCRibbonQuickAccessToolBarDefaultState`使用這個物件的物件[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)方法。

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

建構的快速存取工具列預設狀態物件。

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>備註

根據預設，清單命令的新執行個體[CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)包含是空的。

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

清除 快速存取工具列中的預設命令的清單。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

此函式會移除這個執行個體的所有命令的先前呼叫[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)加入。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
