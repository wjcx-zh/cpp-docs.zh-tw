---
title: CVSListBox 類別
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373183"
---
# <a name="cvslistbox-class"></a>CVSListBox 類別

類別`CVSListBox`支援可編輯的清單控制件。

## <a name="syntax"></a>語法

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CVSListBox:CVSListBox](#cvslistbox)|建構 `CVSListBox` 物件。|
|`CVSListBox::~CVSListBox`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CVSListBox::新增專案](#additem)|將字串新增到清單控制項。 (覆寫 `CVSListBoxBase::AddItem`。)|
|[CVSListBox:編輯項目](#edititem)|對清單控制項項目的文字啟動編輯操作。 (覆寫 `CVSListBoxBase::EditItem`。)|
|[CVSListBox:取得計數](#getcount)|檢索可編輯清單控制件中的字串數。 (覆寫 `CVSListBoxBase::GetCount`。)|
|[CVSListBox:抓取項目資料](#getitemdata)|檢索與可編輯清單控制項關聯的特定於應用程式的 32 位值。 (覆寫 `CVSListBoxBase::GetItemData`。)|
|[CVSListBox:抓取項目文字](#getitemtext)|檢索可編輯清單控制項的文字。 (覆寫 `CVSListBoxBase::GetItemText`。)|
|[CVSListBox::取得塞爾項目](#getselitem)|在可編輯清單控制項中檢索當前選定項的零基索引。 (覆寫 `CVSListBoxBase::GetSelItem`。)|
|`CVSListBox::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 有關詳細資訊和方法語法,請參閱[CWnd::P重新翻譯消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CVSListBoxBase::PreTranslateMessage`。)|
|[CVSListBox:刪除項目](#removeitem)|從可編輯清單控制項中刪除專案。 (覆寫 `CVSListBoxBase::RemoveItem`。)|
|[CVSListBox:選擇項目](#selectitem)|選擇可編輯的清單控制字串。 (覆寫 `CVSListBoxBase::SelectItem`。)|
|[CVSListBox::設定項目資料](#setitemdata)|將特定於應用程式的 32 位值與可編輯的清單控制項關聯。 (覆寫 `CVSListBoxBase::SetItemData`。)|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CVSListBox:取得清單Hwnd](#getlisthwnd)|將句柄返回到當前嵌入的列表檢視控制項。|

## <a name="remarks"></a>備註

該`CVSListBox`類提供一組編輯按鈕,使用戶能夠在清單控制項中創建、修改、刪除或重新排列專案。

以下是可編輯清單控制件的圖片。 第二個清單條目名為"專案 2",用於編輯。

![CVSListBox 控制項](../../mfc/reference/media/cvslistbox.png "CVSListBox 控制項")

如果使用資源編輯器添加可編輯清單控制件,請注意編輯器的**Toolbox**窗格不提供預定義的可編輯清單控制項。 而是添加靜態控件,如**組框**控件。 框架使用靜態控制項作為占位符來指定可編輯清單控制項的大小和位置。

要在對話框範本中使用可編輯的清單控制項,請在對話方塊類中`CVSListBox`聲明變數。 要支援變數和控件之間的數據交換,請在對話方塊`DDX_Control``DoDataExchange`的方法中定義一個宏條目。 預設情況下,無需編輯按鈕即可創建可編輯的清單控制項。 使用繼承的 CVSListBoxBase::設定標準按鈕方法啟用編輯按鈕。

有關詳細資訊,請參閱範例目錄、`New Controls`範例、Page3.cpp 和 Page3.h 檔。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>需求

**標題:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox::新增專案

將字串新增到清單控制項。

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*斯特裡克斯特*<br/>
[在]對字串的引用。

*dwData*<br/>
[在]與字串關聯的特定於應用程式的 32 位值。 預設值為 0。

*iIndex*<br/>
[在]將保存字串的位置的零基索引。 如果*iIndex*參數為 -1,則字串將添加到清單的末尾。 預設值為 -1。

### <a name="return-value"></a>傳回值

字串在清單控制項中位置的零基索引。

### <a name="remarks"></a>備註

使用[CVSListBox::getItemData](#getitemdata)方法檢索*dwData*參數指定的值。 此值可以是特定於應用程式的整數或指向其他數據的指標。

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox:CVSListBox

建構 `CVSListBox` 物件。

```
CVSListBox();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox:編輯項目

對清單控制項項目的文字啟動編輯操作。

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單控制項項的零基索引。

### <a name="return-value"></a>傳回值

如果編輯操作成功啟動,則為 TRUE;如果編輯操作成功啟動,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

用戶通過雙擊項目的標籤,或在專案具有焦點時按**F2**或**空格鍵**來啟動編輯操作。

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox:取得計數

檢索可編輯清單控制件中的字串數。

```
virtual int GetCount() const;
```

### <a name="return-value"></a>傳回值

清單控制項中的項目數。

### <a name="remarks"></a>備註

請注意,計數大於最後一個項的索引值,因為索引是零基的。

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox:抓取項目資料

檢索與可編輯清單控制項關聯的特定於應用程式的 32 位值。

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]可編輯清單控制項的零基索引。

### <a name="return-value"></a>傳回值

與指定項關聯的 32 位值。

### <a name="remarks"></a>備註

使用[CVSListBox::設定項目資料](#setitemdata)或[CVSListBox:addItem](#additem)方法將 32 位值與清單控制項相關聯。 此值可以是特定於應用程式的整數或指向其他數據的指標。

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox:抓取項目文字

檢索可編輯清單控制項的文字。

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]可編輯清單控制項的零基索引。

### <a name="return-value"></a>傳回值

包含指定項文字的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox:取得清單Hwnd

將句柄返回到當前嵌入的列表檢視控制項。

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>傳回值

嵌入清單檢視控制項的句柄。

### <a name="remarks"></a>備註

使用此方法檢視類的嵌入式清單檢視控制項的`CVSListBox`句柄。

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::取得塞爾項目

在可編輯清單控制項中檢索當前選定項的零基索引。

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>傳回值

如果此方法成功,則當前選定項的零基索引;否則,-1。

### <a name="remarks"></a>備註

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox:刪除項目

從可編輯清單控制項中刪除專案。

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]可編輯清單控制項的零基索引。

### <a name="return-value"></a>傳回值

如果刪除指定的項,則為 TRUE;如果已刪除指定項,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox:選擇項目

選擇可編輯的清單控制字串。

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
[在]可編輯清單控制項的零基索引。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法選擇指定的項,如果需要,則將項滾動到視圖中。

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::設定項目資料

將特定於應用程式的 32 位值與可編輯的清單控制項關聯。

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]可編輯清單控制項的零基索引。

*dwData*<br/>
[在]32 位值。 此值可以是特定於應用程式的整數或指向其他數據的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
