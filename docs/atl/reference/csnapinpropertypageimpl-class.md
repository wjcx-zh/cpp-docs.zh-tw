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
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496401"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 類別

這個類別會提供用來執行嵌入式管理單元屬性頁物件的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|變更 [**確定] 和 [** **取消**] 按鈕的狀態。|
|[CSnapInPropertyPageImpl::Create](#create)|初始化新建立`CSnapInPropertyPageImpl`的物件。|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|當使用者在使用 wizard 類型的屬性工作表時, 按一下 [**立即**套用] 按鈕時, 由架構呼叫。|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|當使用者在使用 wizard 類型的屬性工作表時按一下 [說明] 按鈕時, 由架構呼叫。|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|當目前的頁面不再使用中時, 由架構呼叫。|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|當使用者按下 [**取消**] 按鈕時, 以及在取消動作執行之前, 由架構呼叫。|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|當使用者在使用 wizard 類型的屬性工作表時, 按一下 [**重設**] 按鈕時由架構呼叫。|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|當目前的頁面變成使用中狀態時, 由架構呼叫。|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|當使用者在使用 wizard 類型的屬性工作表時, 按一下 [**上一頁**] 按鈕時由架構呼叫。|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|當使用者在使用 wizard 類型的屬性工作表時, 按一下 [**完成**] 按鈕時由架構呼叫。|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|當使用者在使用 wizard 類型的屬性工作表時, 按一下 [**下一步]** 按鈕時由架構呼叫。|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|將目前的訊息轉送至屬性工作表的所有頁面。|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|呼叫以啟用或停用 [**立即**套用] 按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|`CSnapInPropertyPageImpl`物件所`PROPSHEETPAGE`使用的 Windows 結構。|

## <a name="remarks"></a>備註

`CSnapInPropertyPageImpl`提供嵌入式管理單元屬性頁物件的基本執行。 嵌入式管理單元屬性頁的基本功能是使用數個不同的介面和對應類型來執行。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>需求

**標頭:** atlsnap。h

##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

在對模式屬性工作表的頁面中的資料進行無法復原的變更之後, 呼叫此函式。

```
void CancelToClose();
```

### <a name="remarks"></a>備註

此函式會變更 [**確定]** 按鈕, 以**關閉**並停用 [**取消**] 按鈕。 這種變更會向使用者通知變更為永久性, 而且無法取消修改。

成員函式不會在非模式屬性工作表中執行任何操作, 因為非模式屬性工作表預設不會有 [取消] 按鈕。 `CancelToClose`

##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

建構 `CSnapInPropertyPageImpl` 物件。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>參數

*lpszTitle*<br/>
在屬性頁的標題。

### <a name="remarks"></a>備註

若要初始化基礎結構, 請呼叫[CSnapInPropertyPageImpl:: Create](#create)。

##  <a name="create"></a>CSnapInPropertyPageImpl:: Create

呼叫此函式以初始化屬性頁的基礎結構。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>傳回值

`PROPSHEETPAGE`結構的控制碼, 其中包含新建立之屬性工作表的屬性。

### <a name="remarks"></a>備註

呼叫此函式之前, 您應該先呼叫[CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) 。

##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`是其成員儲存特性的`PROPSHEETPAGE`結構。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構來初始化屬性頁在建立後的外觀。

如需此結構的詳細資訊, 包括其成員的清單, 請參閱 Windows SDK 中的[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) 。

##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

當使用者按一下 [**確定]** 或 [**立即**套用] 按鈕時, 就會呼叫這個成員函式。

```
BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受變更, 則為非零值;否則為0。

### <a name="remarks"></a>備註

在`OnApply`可由架構呼叫之前, 您必須先呼叫`SetModified` , 並將其參數設定為 TRUE。 這會在使用者于屬性頁上進行變更時立即啟用 [**立即**套用] 按鈕。

覆寫此成員函式, 以指定當使用者按一下 [**立即**套用] 按鈕時, 您的程式所採取的動作。 覆寫時, 函式應該傳回 TRUE 以接受變更, FALSE 則會防止變更生效。

的預設實`OnApply`值會傳回 TRUE。

##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

當使用者按一下屬性頁的 [說明] 按鈕時, 就會呼叫這個成員函式。

```
void OnHelp();
```

### <a name="remarks"></a>備註

覆寫此成員函式以顯示內容頁的說明。

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

當頁面不再是作用中頁面時, 會呼叫這個成員函式。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

如果成功更新資料, 則為非零值;否則為0。

### <a name="remarks"></a>備註

覆寫這個成員函式以執行特殊的資料驗證工作。

##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl:: OnQueryCancel

此成員函式會在使用者按一下 [**取消**] 按鈕時, 以及在取消動作執行之前呼叫。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

允許取消作業的非零值;否則為0。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當使用者按一下 [**取消**] 按鈕時, 程式所採取的動作。

的預設實`OnQueryCancel`值會傳回 TRUE。

##  <a name="onreset"></a>CSnapInPropertyPageImpl:: OnReset

當使用者按一下 [**取消**] 按鈕時, 就會呼叫這個成員函式。

```
void OnReset();
```

### <a name="remarks"></a>備註

呼叫此函式時, 使用者先前按一下 [**立即**套用] 按鈕所做的所有屬性頁變更都會被捨棄, 且屬性工作表會保留焦點。

覆寫這個成員函式, 以指定當使用者按一下 [**取消**] 按鈕時, 程式所採取的動作。

##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

當使用者選擇頁面時, 會呼叫這個成員函式, 並成為使用中的頁面。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

如果已成功設定頁面, 則為非零值;否則為0。

### <a name="remarks"></a>備註

當網頁啟動時, 覆寫此成員函式以執行工作。 此成員函式的覆寫應該在進行任何其他處理之前呼叫預設版本。

預設的實值會傳回 TRUE。

##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

當使用者按一下 wizard 中的 [**上一頁**] 按鈕時, 就會呼叫這個成員函式。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>傳回值

- 0會自動前進到上一頁。

- -1 以防止頁面變更。

若要跳至下一頁以外的頁面, 請傳回要顯示之對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當按一下 [**上一頁**] 按鈕時, 使用者必須採取的動作。

##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

當使用者按一下 wizard 中的 [**完成]** 按鈕時, 就會呼叫這個成員函式。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果在 wizard 完成時終結屬性工作表則為非零, 否則為。否則為零。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當按一下 [**完成]** 按鈕時, 使用者必須採取的動作。

##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

當使用者按一下嚮導中的 [**下一步**] 按鈕時, 就會呼叫這個成員函式。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>傳回值

- 0會自動前進到下一個頁面。

- -1 以防止頁面變更。

若要跳至下一頁以外的頁面, 請傳回要顯示之對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當按一下 [**下一步]** 按鈕時, 使用者必須採取的動作。

##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

呼叫這個成員函式, 將訊息轉送至屬性工作表中的每個頁面。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
在指定與訊息相關的其他資訊。

*lParam*<br/>
在指定與訊息相關的其他資訊。

### <a name="return-value"></a>傳回值

如果不應將訊息轉送至下一個屬性頁, 則為非零值。否則為零。

### <a name="remarks"></a>備註

如果頁面傳回非零值, 則屬性工作表不會將訊息傳送至後續頁面。

##  <a name="setmodified"></a>CSnapInPropertyPageImpl:: SetModified

根據屬性頁中的設定是否應該套用至適當的外部物件, 呼叫這個成員函式來啟用或停用 [**立即**套用] 按鈕。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*bChanged*<br/>
在TRUE 表示屬性頁設定自上次套用之後已經修改;FALSE 表示已套用屬性頁設定, 或應予以忽略。

### <a name="remarks"></a>備註

屬性工作表會持續追蹤哪些頁面是「已變更」, 也就是您已呼叫`SetModified( TRUE )`的屬性頁。 如果您呼叫`SetModified( TRUE )`其中一個頁面, 一律會啟用 [立即套用] 按鈕。 當您呼叫`SetModified( FALSE )`其中一個頁面時, 只會停用 [立即套用] 按鈕, 但只有在沒有其他頁面「已變更」時, 才會停用。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
