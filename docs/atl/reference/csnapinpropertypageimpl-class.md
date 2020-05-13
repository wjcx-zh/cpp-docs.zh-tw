---
title: 快照財產頁頁課
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747574"
---
# <a name="csnapinpropertypageimpl-class"></a>快照財產頁頁課

此類提供實現管理單元屬性頁物件的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[快照財產頁頁::CSnapin屬性頁頁](#csnapinpropertypageimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[快照屬性頁頁::取消關閉](#canceltoclose)|更改 **「確定**」和 **「取消」** 按鈕的狀態。|
|[CSnapIn屬性頁頁::建立](#create)|初始化新創建`CSnapInPropertyPageImpl`的物件。|
|[CSnapin屬性頁頁::打開應用](#onapply)|當使用者使用嚮導類型的屬性表按下「**立即應用」** 按鈕時,由框架呼叫。|
|[CSnapin屬性頁頁::上説明](#onhelp)|當使用者使用嚮導類型的屬性表按**下 「説明**」按鈕時,由框架呼叫。|
|[快照財產頁頁::在基爾基活動](#onkillactive)|當當前頁面不再處於活動狀態時,由框架調用。|
|[CSnapin 屬性頁頁::打開查詢取消](#onquerycancel)|當使用者按下 **「取消」** 按鈕時和取消發生之前,由框架調用。|
|[快照屬性頁頁::開啟](#onreset)|當使用者使用嚮導類型的屬性表按**下「重置」** 按鈕時,由框架呼叫。|
|[快照財產頁頁::打開活動](#onsetactive)|當當前頁面處於活動狀態時,由框架調用。|
|[CSnapin屬性頁頁::在嚮導背面](#onwizardback)|當使用者在使用嚮導類型的屬性表時按下 **「後退**」按鈕時,由框架呼叫。|
|[CSnapin屬性頁頁::在嚮導完成](#onwizardfinish)|當使用者使用精靈類型的屬性表按下 **「完成」** 按鈕時,由框架呼叫。|
|[CSnapin屬性頁頁::在嚮導下一個](#onwizardnext)|當使用者使用嚮導類型的屬性表按**下 「下一步**」按鈕時,由框架調用。|
|[CSnapIn屬性頁::查詢兄弟](#querysiblings)|將當前消息轉發到屬性表的所有頁面。|
|[CSnapin屬性頁頁::設定修改](#setmodified)|呼叫以啟動或停用「**立即應用」** 按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSnapIn屬性頁頁::m_psp](#m_psp)|`CSnapInPropertyPageImpl`物件使用的 Windows`PROPSHEETPAGE`結構。|

## <a name="remarks"></a>備註

`CSnapInPropertyPageImpl`為管理單元屬性頁物件提供了基本實現。 管理單元屬性頁的基本功能使用多個不同的介面和映射類型實現。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>需求

**標題:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>快照屬性頁頁::取消關閉

對模態屬性表頁面中的數據進行了不可恢復的更改後,請調用此函數。

```cpp
void CancelToClose();
```

### <a name="remarks"></a>備註

此功能將「**確定」** 按鈕更改為 **「關閉**」 關閉 「關閉」 關閉 「**取消」** 按鈕。 此更改提醒使用者更改是永久性的,並且無法取消修改。

成員`CancelToClose`函數在無模式屬性表中不執行任何操作,因為預設情況下,無模式屬性表沒有 **"取消"** 按鈕。

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>快照財產頁頁::CSnapin屬性頁頁

建構 `CSnapInPropertyPageImpl` 物件。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
[在]屬性頁的標題。

### <a name="remarks"></a>備註

要初始化基礎結構,請致電[CSnapInPropertypageimpl::創建](#create)。

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapIn屬性頁頁::建立

調用此函數以初始化屬性頁的基礎結構。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>傳回值

包含新創建屬性`PROPSHEETPAGE`表屬性的結構的句柄。

### <a name="remarks"></a>備註

在調用此函數之前,應首先調用[CSnapInpropertypageimpl::CSnapInPropertypageimpl。](#csnapinpropertypageimpl)

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapIn屬性頁頁::m_psp

`m_psp`是其成員儲存的特性的結構`PROPSHEETPAGE`。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構在構造屬性頁后初始化屬性頁的外觀。

有關此結構的詳細資訊(包括其成員的清單),請參閱 Windows SDK 中的[PROPSHEETPAGE。](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3)

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapin屬性頁頁::打開應用

當使用者按下 **「確定」** 或「**立即應用」** 按鈕時,將呼叫此成員函數。

```
BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受更改,則非零;否則 0。

### <a name="remarks"></a>備註

在`OnApply`框架可以調用之前,必須調用`SetModified`其參數並將其設置為 TRUE。 當使用者在屬性頁上進行更改時,這將啟動"**立即應用"** 按鈕。

覆蓋此成員函數,以指定當使用者按下「**立即應用」** 按鈕時程式執行的操作。 重寫時,函數應返回 TRUE 以接受更改和 FALSE,以防止更改生效。

預設實現`OnApply`返回 TRUE。

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapin屬性頁頁::上説明

當使用者單擊屬性頁的 **「幫助**」按鈕時,將調用此成員函數。

```cpp
void OnHelp();
```

### <a name="remarks"></a>備註

覆蓋此成員函數以顯示屬性頁的説明。

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>快照財產頁頁::在基爾基活動

當頁面不再是活動頁時,將調用此成員函數。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

如果數據已成功更新,則非零;否則 0。

### <a name="remarks"></a>備註

重寫此成員函數以執行特殊的資料驗證任務。

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapin 屬性頁頁::打開查詢取消

當用戶按下 **「取消」** 按鈕並在執行取消操作之前調用此成員函數。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

非零以允許取消操作;否則 0。

### <a name="remarks"></a>備註

覆蓋此成員函數以指定程式在使用者按下 **「取消」** 按鈕時執行的操作。

預設實現`OnQueryCancel`返回 TRUE。

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>快照屬性頁頁::開啟

當使用者按下 **「取消」** 按鈕時,將調用此成員函數。

```cpp
void OnReset();
```

### <a name="remarks"></a>備註

呼叫此函數時,將放棄使用者以前按一下 **「立即應用」** 按鈕時所做的所有屬性頁的更改,並且屬性表將保留焦點。

覆蓋此成員函數以指定當使用者按下 **「取消」** 按鈕時程式執行的操作。

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>快照財產頁頁::打開活動

當用戶選擇該頁並成為活動頁時,將調用此成員函數。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

如果頁面已成功設置為活動,則非零;否則 0。

### <a name="remarks"></a>備註

覆蓋此成員函數,以在啟動頁面時執行任務。 在完成任何其他處理之前,應調用預設版本。

預設實現返回 TRUE。

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapin屬性頁頁::在嚮導背面

當用戶單擊嚮導中的 **「後退」** 按鈕時,將調用此成員函數。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>傳回值

- 0 自動前進到上一頁。

- -1 以防止頁面更改。

要跳到下一個頁面以外的頁面,傳回要顯示的對話框的標識符。

### <a name="remarks"></a>備註

重寫此成員函數以指定使用者按下 **「後退」** 按鈕時必須執行的操作。

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapin屬性頁頁::在嚮導完成

當使用者按一下精靈中的 **「完成」** 按鈕時,將呼叫此成員函數。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果屬性表在嚮導完成時銷毀,則非零;否則為零。

### <a name="remarks"></a>備註

覆蓋此成員函數以指定使用者在按下 **「完成」 按鈕**時必須執行的操作。

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapin屬性頁頁::在嚮導下一個

當使用者按一下精靈中的 **「下一步**」按鈕時,將呼叫此成員函數。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>傳回值

- 0 自動前進到下一頁。

- -1 以防止頁面更改。

要跳到下一個頁面以外的頁面,傳回要顯示的對話框的標識符。

### <a name="remarks"></a>備註

重寫此成員函數以指定使用者在按下「**下一步**」按鈕時必須執行的操作。

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapIn屬性頁::查詢兄弟

調用此成員函數將消息轉發到屬性表中的每個頁面。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
[在]指定其他與消息相關的資訊。

*lParam*<br/>
[在]指定其他與消息相關的資訊。

### <a name="return-value"></a>傳回值

如果消息不應轉發到下一個屬性頁,則為非零;否則為零。

### <a name="remarks"></a>備註

如果頁面返回非零值,則屬性表不會將消息發送到後續頁面。

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapin屬性頁頁::設定修改

呼叫此成員函數以啟用或禁用 **「立即應用程式」** 按鈕,具體取決於屬性頁中的設定是否應應用於相應的外部物件。

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*b 已變更*<br/>
[在]TRUE 以指示自上次應用屬性頁設置以來已修改屬性頁設置;FALSE 以指示已應用屬性頁設置,或應忽略。

### <a name="remarks"></a>備註

屬性表追蹤哪些頁面是「臟」的,即您為其調用`SetModified( TRUE )`的屬性頁。 如果調用`SetModified( TRUE )`其中一個頁面,則始終啟用"**立即應用"** 按鈕。 當您調用`SetModified( FALSE )`其中一個頁面時,將禁用"**立即應用"** 按鈕,但前提是其他頁面均未"臟"。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
