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
ms.openlocfilehash: 6a33f5b64c5094bfe2ca2ff259b5cd8654058ed3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502237"
---
# <a name="cvslistbox-class"></a>CVSListBox 類別

`CVSListBox`類別支援可編輯的清單控制項。

## <a name="syntax"></a>語法

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|建構 `CVSListBox` 物件。|
|`CVSListBox::~CVSListBox`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|將字串新增至清單控制項。 (覆寫 `CVSListBoxBase::AddItem`。)|
|[CVSListBox::EditItem](#edititem)|對清單控制項專案的文字開始編輯作業。 (覆寫 `CVSListBoxBase::EditItem`。)|
|[CVSListBox::GetCount](#getcount)|抓取可編輯清單控制項中的字串數目。 (覆寫 `CVSListBoxBase::GetCount`。)|
|[CVSListBox::GetItemData](#getitemdata)|抓取與可編輯清單控制項專案相關聯的應用程式特定32位值。 (覆寫 `CVSListBoxBase::GetItemData`。)|
|[CVSListBox::GetItemText](#getitemtext)|抓取可編輯清單控制項專案的文字。 (覆寫 `CVSListBoxBase::GetItemText`。)|
|[CVSListBox::GetSelItem](#getselitem)|抓取可編輯清單控制項中目前所選取專案之以零為起始的索引。 (覆寫 `CVSListBoxBase::GetSelItem`。)|
|`CVSListBox::PreTranslateMessage`|會先轉譯視窗訊息, 再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需詳細資訊和方法語法, 請參閱[CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CVSListBoxBase::PreTranslateMessage`。)|
|[CVSListBox::RemoveItem](#removeitem)|從可編輯的清單控制項中移除專案。 (覆寫 `CVSListBoxBase::RemoveItem`。)|
|[CVSListBox::SelectItem](#selectitem)|選取可編輯的清單控制項字串。 (覆寫 `CVSListBoxBase::SelectItem`。)|
|[CVSListBox::SetItemData](#setitemdata)|將應用程式特定的32位值與可編輯的清單控制項專案產生關聯。 (覆寫 `CVSListBoxBase::SetItemData`。)|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|傳回目前內嵌清單視圖控制項的控制碼。|

## <a name="remarks"></a>備註

`CVSListBox`類別提供一組 [編輯] 按鈕, 可讓使用者建立、修改、刪除或重新排列清單控制項中的專案。

以下是可編輯清單控制項的圖片。 第二個清單專案 (標題為 "Item2") 是選取來進行編輯。

![CVSListBox 控制項](../../mfc/reference/media/cvslistbox.png "CVSListBox 控制項")

如果您使用資源編輯器來加入可編輯的清單控制項, 請注意編輯器的 [**工具箱**] 窗格並未提供預先定義的可編輯清單控制項。 相反地, 請加入靜態控制項, 例如 [**群組方塊**] 控制項。 架構會使用靜態控制項做為預留位置, 以指定可編輯清單控制項的大小和位置。

若要在對話方塊範本中使用可編輯的清單控制項, 請`CVSListBox`在您的對話方塊類別中宣告變數。 若要支援變數和控制項之間的資料交換, 請`DDX_Control` `DoDataExchange`在對話方塊的方法中定義宏專案。 根據預設, 會建立不含 [編輯] 按鈕的可編輯清單控制項。 使用繼承的 CVSListBoxBase:: SetStandardButtons 方法來啟用 [編輯] 按鈕。

如需詳細資訊, 請參閱範例目錄, `New Controls`範例, Page3 .cpp 和 Page3 檔案。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>需求

**標頭:** afxvslistbox。h

##  <a name="additem"></a>CVSListBox:: AddItem

將字串新增至清單控制項。

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*strIext*<br/>
在字串的參考。

*dwData*<br/>
在與字串相關聯的應用程式特定32位值。 預設值為 0。

*iIndex*<br/>
在要保存字串之位置的以零為起始的索引。 如果*iIndex*參數為-1, 則字串會加入至清單的結尾。 預設值為 -1。

### <a name="return-value"></a>傳回值

清單控制項中字串位置之以零為起始的索引。

### <a name="remarks"></a>備註

使用[CVSListBox:: GetItemData](#getitemdata)方法來取出*dwData*參數所指定的值。 此值可以是應用程式特定的整數或其他資料的指標。

##  <a name="cvslistbox"></a>CVSListBox:: CVSListBox

建構 `CVSListBox` 物件。

```
CVSListBox();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="edititem"></a>CVSListBox:: EditItem

對清單控制項專案的文字開始編輯作業。

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在清單控制項專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果編輯作業成功啟動, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用者可以按兩下專案的標籤, 或在專案有焦點時按**F2**或**空格鍵**鍵來啟動編輯作業。

##  <a name="getcount"></a>CVSListBox:: GetCount

抓取可編輯清單控制項中的字串數目。

```
virtual int GetCount() const;
```

### <a name="return-value"></a>傳回值

清單控制項中的項目數。

### <a name="remarks"></a>備註

請注意, 此計數會大於最後一個專案的索引值, 因為索引是以零為起始。

##  <a name="getitemdata"></a>CVSListBox:: GetItemData

抓取與可編輯清單控制項專案相關聯的應用程式特定32位值。

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在可編輯清單控制項專案之以零為基底的索引。

### <a name="return-value"></a>傳回值

與指定專案相關聯的32位值。

### <a name="remarks"></a>備註

使用[CVSListBox:: SetItemData](#setitemdata)或[CVSListBox:: AddItem](#additem)方法, 讓32位值與清單控制項專案產生關聯。 此值可以是應用程式特定的整數或其他資料的指標。

##  <a name="getitemtext"></a>CVSListBox:: GetItemText

抓取可編輯清單控制項專案的文字。

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在可編輯清單控制項專案之以零為基底的索引。

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含指定專案的文字。

### <a name="remarks"></a>備註

##  <a name="getlisthwnd"></a>CVSListBox:: GetListHwnd

傳回目前內嵌清單視圖控制項的控制碼。

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>傳回值

內嵌清單視圖控制項的控制碼。

### <a name="remarks"></a>備註

使用這個方法來抓取支援`CVSListBox`類別之內嵌清單視圖控制項的控制碼。

##  <a name="getselitem"></a>CVSListBox:: GetSelItem

抓取可編輯清單控制項中目前所選取專案之以零為起始的索引。

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>傳回值

如果此方法成功, 則為目前所選取專案之以零為起始的索引;否則為-1。

### <a name="remarks"></a>備註

##  <a name="removeitem"></a>CVSListBox:: RemoveItem

從可編輯的清單控制項中移除專案。

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在可編輯清單控制項專案之以零為基底的索引。

### <a name="return-value"></a>傳回值

如果已移除指定的專案, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="selectitem"></a>CVSListBox:: SelectItem

選取可編輯的清單控制項字串。

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
在可編輯清單控制項專案之以零為基底的索引。

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會選取指定的專案, 如果需要, 請將專案滾動到 view。

##  <a name="setitemdata"></a>CVSListBox:: SetItemData

將應用程式特定的32位值與可編輯的清單控制項專案產生關聯。

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在可編輯清單控制項專案之以零為基底的索引。

*dwData*<br/>
在32位的值。 此值可以是應用程式特定的整數或其他資料的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
