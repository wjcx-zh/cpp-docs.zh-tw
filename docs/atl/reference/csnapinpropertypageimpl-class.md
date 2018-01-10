---
title: "CSnapInPropertyPageImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fc1135f02c31c644d7d149900bbaa755a52c579
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 類別
這個類別會提供實作嵌入式管理單元屬性頁物件的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|狀態變更**確定**和**取消**按鈕。|  
|[CSnapInPropertyPageImpl::Create](#create)|初始化新建立`CSnapInPropertyPageImpl`物件。|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|當使用者按一下時由架構呼叫**立即套用**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|當使用者按一下時由架構呼叫**協助**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|無法再使用目前的頁面時，由架構呼叫。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|當使用者按一下時由架構呼叫**取消** 按鈕，取消動作發生之前。|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|當使用者按一下時由架構呼叫**重設**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|當目前的頁面會變成作用中時，由架構呼叫。|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|當使用者按一下時由架構呼叫**回**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|當使用者按一下時由架構呼叫**完成**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|當使用者按一下時由架構呼叫`Next`使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|將轉送至屬性工作表的所有頁面目前的訊息。|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|啟用或停用呼叫**立即套用** 按鈕。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE**所使用的結構`CSnapInPropertyPageImpl`物件。|  
  
## <a name="remarks"></a>備註  
 `CSnapInPropertyPageImpl`提供基本實作嵌入式管理單元 屬性頁面物件。 嵌入式管理單元屬性頁的基本功能會使用數個不同的介面實作，並將對應型別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsnap.h  
  
##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 無法復原的變更建立強制回應屬性工作表頁面中的資料之後，請呼叫此函式。  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>備註  
 此函式會變更**確定**按鈕**關閉**和停用**取消** 按鈕。 此變更的警示的變更是永久的修改使用者無法取消。  
  
 `CancelToClose`成員函式不做任何動作在非強制回應屬性工作表中，因為非強制回應屬性工作表並沒有**取消**預設按鈕。  
  
##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 建構 `CSnapInPropertyPageImpl` 物件。  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszTitle`  
 [in]屬性頁的標題。  
  
### <a name="remarks"></a>備註  
 若要初始化的基礎結構，請呼叫[CSnapInPropertyPageImpl::Create](#create)。  
  
##  <a name="create"></a>CSnapInPropertyPageImpl::Create  
 呼叫此函式來初始化屬性頁的基礎結構。  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼**PROPSHEETPAGE**結構，其中包含新建立的屬性工作表的屬性。  
  
### <a name="remarks"></a>備註  
 您應該先呼叫[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前呼叫這個函式。  
  
##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`是一種結構的成員儲存的特性**PROPSHEETPAGE**。  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>備註  
 您可以使用此結構來建構後即初始化屬性頁面的外觀。  
  
 如需有關此結構，包括其成員的清單，請參閱[PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151) Windows SDK 中。  
  
##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 此成員函式在使用者按一下時呼叫**確定**或**立即套用** 按鈕。  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果所做的變更已被接受。否則便是 0。  
  
### <a name="remarks"></a>備註  
 之前`OnApply`可以呼叫由架構中，您必須先呼叫`SetModified`並將其參數設定為**TRUE**。 這會啟動**立即套用**按鈕一旦使用者在屬性頁上進行變更。  
  
 覆寫此成員函式，來指定您的程式會在使用者按一下時的動作**立即套用** 按鈕。 函式覆寫時，應傳回**TRUE**接受變更並**FALSE**以防止變更生效。  
  
 預設實作`OnApply`傳回**TRUE**。  
  
##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 此成員函式在使用者按一下時呼叫**協助**屬性頁 按鈕。  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以顯示屬性頁的說明。  
  
##  <a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 當頁面不再使用中的頁面，會呼叫此成員函式。  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功; 更新資料否則便是 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以執行特殊的資料驗證工作。  
  
##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 此成員函式在使用者按一下時呼叫**取消**按鈕，然後取消之前已採取動作的地方。  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，允許取消作業。否則便是 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以指定程式會在使用者按一下時的動作**取消** 按鈕。  
  
 預設實作`OnQueryCancel`傳回**TRUE**。  
  
##  <a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 此成員函式在使用者按一下時呼叫**取消** 按鈕。  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>備註  
 當呼叫此函式時，會變更為使用者先前按一下所做的所有屬性頁**立即套用**按鈕會予以捨棄，而且屬性工作表會保留焦點。  
  
 覆寫此成員函式，來指定程式會在使用者按一下時的動作**取消** 按鈕。  
  
##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 此成員函式稱為頁面由使用者選擇後會變成使用中的頁面。  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果頁面已成功設定作用中。否則便是 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來啟動頁面時執行工作。 此成員函式的覆寫應該呼叫的預設版本之前會進行任何其他處理。  
  
 預設實作會傳回**TRUE**。  
  
##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 此成員函式在使用者按一下時呼叫**回**在精靈中的按鈕。  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>傳回值  
  
-   0 表示自動前進到前一頁。  
  
-   若要防止頁面變更為-1。  
  
 若要跳至下一個以外的頁面，請傳回對話方塊顯示的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取某些動作**回**按鈕。  
  
##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 此成員函式在使用者按一下時呼叫**完成**在精靈中的按鈕。  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果在精靈完成時，系統會終結屬性工作表否則為零。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取某些動作**完成**按鈕。  
  
##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 此成員函式在使用者按一下時呼叫`Next`在精靈中的按鈕。  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>傳回值  
  
-   0 表示自動前進到下一個頁面。  
  
-   若要防止頁面變更為-1。  
  
 若要跳至下一個以外的頁面，請傳回對話方塊顯示的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取某些動作`Next`按鈕。  
  
##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 呼叫此成員函式轉送至屬性工作表中的每個頁面的訊息。  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `wParam`  
 [in]指定訊息相關的其他資訊。  
  
 `lParam`  
 [in]指定訊息相關的其他資訊。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果不應該將訊息轉送至下一步 屬性頁。否則為零。  
  
### <a name="remarks"></a>備註  
 如果頁面傳回則為非零值，屬性工作表不會傳送訊息到後續的頁面。  
  
##  <a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 呼叫此成員函式，啟用或停用**立即套用**按鈕時，根據屬性頁中的設定是否應該套用到適當的外部物件。  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bChanged`  
 [in]**TRUE**表示屬性頁設定，已修改這些交易套用; 最後一次**FALSE** ，表示屬性頁設定已套用，或應予忽略。  
  
### <a name="remarks"></a>備註  
 屬性工作表會持續的追蹤頁面的 「 有所變更 」，也就是，您所呼叫的屬性頁**SetModified (TRUE)**。 **立即套用**按鈕將一律會啟用，如果您呼叫**SetModified (TRUE)**的其中一個頁面。 **立即套用**將停用 按鈕，當您呼叫**SetModified (FALSE)**的其中一個頁面，但如果沒有任何其他網頁 「 有所變更 」。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
