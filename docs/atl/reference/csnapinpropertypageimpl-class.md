---
title: CSnapInPropertyPageImpl 類別
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
ms.openlocfilehash: ea79a5624937b27fe69be2c15bac3a0c40592252
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575739"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 類別

這個類別提供方法實作嵌入式管理單元 屬性頁面物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|變更的狀態 **[確定]** 並**取消**按鈕。|
|[CSnapInPropertyPageImpl::Create](#create)|初始化新建立`CSnapInPropertyPageImpl`物件。|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|由架構呼叫，當使用者按一下**立即套用**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|由架構呼叫，當使用者按一下**協助**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|當目前的頁面已不再使用中時，由架構呼叫。|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|由架構呼叫，當使用者按一下**取消** 按鈕，並取消動作發生之前。|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|由架構呼叫，當使用者按一下**重設**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|當目前的頁面會變成作用中時，由架構呼叫。|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|由架構呼叫，當使用者按一下**回**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|由架構呼叫，當使用者按一下**完成**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|由架構呼叫，當使用者按一下**下一步**使用精靈類型的屬性工作表 按鈕。|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|將轉送至屬性工作表的所有頁面目前的訊息。|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|啟用或停用的通話**立即套用** 按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows`PROPSHEETPAGE`所使用的結構`CSnapInPropertyPageImpl`物件。|

## <a name="remarks"></a>備註

`CSnapInPropertyPageImpl` 提供基本的實作嵌入式管理單元 屬性頁面物件。 嵌入式管理單元屬性頁的基本功能使用數個不同的介面實作，並將型別對應。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>需求

**標頭：** atlsnap.h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

無法復原的變更已對的強制回應屬性工作表頁中的資料之後，請呼叫此函式。

```
void CancelToClose();
```

### <a name="remarks"></a>備註

此函式會變更**確定**按鈕來**關閉**，並停用**取消** 按鈕。 這項變更無法取消變更是永久的修改使用者的警示。

`CancelToClose`成員函式不在非強制回應屬性工作表中，執行任何動作，因為非強制回應屬性工作表並沒有**取消**預設按鈕。

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

建構 `CSnapInPropertyPageImpl` 物件。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
[in]屬性頁的標題。

### <a name="remarks"></a>備註

若要初始化的基礎結構，請呼叫[CSnapInPropertyPageImpl::Create](#create)。

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

呼叫此函式來初始化的屬性頁的基礎結構。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>傳回值

控制代碼`PROPSHEETPAGE`結構，其中包含新建立的屬性工作表的屬性。

### <a name="remarks"></a>備註

您應該先呼叫[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前呼叫這個函式。

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp` 是其成員儲存的特性結構`PROPSHEETPAGE`。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構來建構後即初始化屬性頁面的外觀。

如需這個結構，包括其成員，清單的詳細資訊，請參閱[PROPSHEETPAGE](https://msdn.microsoft.com/library/aa815151) Windows SDK 中。

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

此成員函式在使用者按一下時呼叫**確定**或**立即套用** 按鈕。

```
BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受變更，為非零否則為 0。

### <a name="remarks"></a>備註

再`OnApply`可以呼叫由架構中，您必須先呼叫`SetModified`並設定其參數為 TRUE。 這會啟動**立即套用**按鈕，使用者會在 [屬性] 頁面上進行變更。

此成員函式，指定您的程式在使用者按一下時所採取的動作會覆寫**立即套用** 按鈕。 覆寫時，此函數應該傳回 TRUE，以接受變更，而 false 則會防止變更生效。

預設實作`OnApply`，則傳回 TRUE。

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

此成員函式在使用者按一下時呼叫**協助**屬性頁 按鈕。

```
void OnHelp();
```

### <a name="remarks"></a>備註

覆寫此成員函式，以顯示 [屬性] 頁面的說明。

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

頁面已不再使用中的頁面時，會呼叫此成員函式。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

如果資料已成功; 更新為非零否則為 0。

### <a name="remarks"></a>備註

覆寫此成員函式，以執行特殊的資料驗證工作。

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

此成員函式在使用者按一下時呼叫**取消**按鈕，並取消之前採取動作的地方。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

非零值，以允許取消作業;否則為 0。

### <a name="remarks"></a>備註

此成員函式，來指定程式會在使用者按一下的動作會覆寫**取消** 按鈕。

預設實作`OnQueryCancel`，則傳回 TRUE。

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

此成員函式在使用者按一下時呼叫**取消** 按鈕。

```
void OnReset();
```

### <a name="remarks"></a>備註

呼叫此函式時，變更先前按一下使用者所做的所有屬性頁**立即套用**按鈕都會被捨棄，並將屬性工作表保留焦點。

此成員函式，指定當使用者按一下時，程式會採用的動作會覆寫**取消** 按鈕。

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

當頁面由使用者選擇而變成使用中的頁面，被呼叫此成員函式。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

非零值，如果頁面已成功設定為使用中;否則為 0。

### <a name="remarks"></a>備註

覆寫此成員函式，來啟動頁面時執行工作。 此成員函式的覆寫其他任何處理完成之前，應該呼叫的預設版本。

預設實作會傳回 TRUE。

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

此成員函式在使用者按一下時呼叫**回**在精靈中的按鈕。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>傳回值

- 0 表示自動前進到前一頁。

- 若要防止頁面變更為-1。

若要跳至下一個以外的頁面，會傳回要顯示的對話方塊中的識別項。

### <a name="remarks"></a>備註

此成員函式，來指定使用者必須時採取某些動作會覆寫**回**按一下按鈕時。

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

此成員函式在使用者按一下時呼叫**完成**在精靈中的按鈕。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果屬性工作表損毀，在精靈完成; 時，非零值。否則為零。

### <a name="remarks"></a>備註

此成員函式，來指定使用者必須時採取某些動作會覆寫**完成**按一下按鈕時。

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

此成員函式在使用者按一下時呼叫**下一步**在精靈中的按鈕。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>傳回值

- 0 表示自動前進到下一個頁面。

- 若要防止頁面變更為-1。

若要跳至下一個以外的頁面，會傳回要顯示的對話方塊中的識別項。

### <a name="remarks"></a>備註

此成員函式，來指定使用者必須時採取某些動作會覆寫**下一步**按一下按鈕時。

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

呼叫此成員函式，來轉送訊息至屬性工作表中的每個頁面。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
[in]指定訊息相關的其他資訊。

*lParam*<br/>
[in]指定訊息相關的其他資訊。

### <a name="return-value"></a>傳回值

如果訊息應該不會轉送到下一步 的 屬性 頁面中，為非零否則為零。

### <a name="remarks"></a>備註

如果頁面傳回非零值，屬性工作表不會傳送訊息至後續頁面。

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

呼叫此成員函式，啟用或停用**立即套用**按鈕時，根據是否在屬性頁中的設定應該套用到適當的外部物件。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*bChanged*<br/>
[in]TRUE 表示的屬性頁設定已遭到修改這些交易套用; 最後一次如果為 false，則表示屬性頁設定已套用，或應該予以忽略。

### <a name="remarks"></a>備註

屬性工作表會保留頁面的 「 變更 」，也就是追蹤、 屬性頁，您必須呼叫`SetModified( TRUE )`。 **立即套用**按鈕將一律會啟用，如果您呼叫`SetModified( TRUE )`的其中一個頁面。 **立即套用**會停用 按鈕，當您呼叫`SetModified( FALSE )`的其中一個頁面，但如果沒有任何其他頁面時才 「 中途 」。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
