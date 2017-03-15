---
title: "CSnapInPropertyPageImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f5db4d0742a423e9574db2a4268a9376491b2ed2
ms.lasthandoff: 02/24/2017

---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 類別
這個類別提供方法來實作嵌入式管理單元 屬性頁面物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
CSnapInPropertyPageImpl : public CDialogImplBase
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|目的狀態變更**確定**和**取消**按鈕。|  
|[CSnapInPropertyPageImpl::Create](#create)|初始化新建立`CSnapInPropertyPageImpl`物件。|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|當使用者按一下時，由框架呼叫**立即套用**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|當使用者按一下時，由框架呼叫**協助**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|不會再使用目前的頁面時，由架構呼叫。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|當使用者按一下時，由框架呼叫**取消** 按鈕，取消動作發生之前。|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|當使用者按一下時，由框架呼叫**重設**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|啟動目前的頁面時，由架構呼叫。|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|當使用者按一下時，由框架呼叫**回**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|當使用者按一下時，由框架呼叫**完成**使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|當使用者按一下時，由框架呼叫`Next`使用精靈類型的屬性工作表 按鈕。|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|會將轉寄至屬性工作表的所有頁面目前的訊息。|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|啟用或停用呼叫**立即套用** 按鈕。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE**所用結構`CSnapInPropertyPageImpl`物件。|  
  
## <a name="remarks"></a>備註  
 `CSnapInPropertyPageImpl`提供的嵌入式管理單元屬性 page 物件的基本實作。 嵌入式管理單元屬性頁的基本功能使用數個不同的介面實作，並將型別對應。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsnap.h  
  
##  <a name="a-namecanceltoclosea--csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 無法復原的變更已對非強制回應屬性工作表頁中的資料之後，請呼叫此函式。  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>備註  
 此函式會變更**確定**按鈕**關閉**和停用**取消** 按鈕。 此變更的警示無法取消使用者的變更是永久的所做的修改。  
  
 `CancelToClose`成員函式不做任何動作在非強制回應屬性工作表中，因為非強制回應屬性工作表沒有**取消**預設按鈕。  
  
##  <a name="a-namecsnapinpropertypageimpla--csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 建構 `CSnapInPropertyPageImpl` 物件。  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszTitle`  
 [in]屬性頁的標題。  
  
### <a name="remarks"></a>備註  
 若要初始化的基礎結構，呼叫[CSnapInPropertyPageImpl::Create](#create)。  
  
##  <a name="a-namecreatea--csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Create  
 呼叫此函式來初始化屬性頁的基礎結構。  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼**PROPSHEETPAGE**結構，其中包含新建立的屬性工作表的屬性。  
  
### <a name="remarks"></a>備註  
 您應該先呼叫[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前呼叫這個函式。  
  
##  <a name="a-namempspa--csnapinpropertypageimplmpsp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`是一種結構的成員儲存的特性**PROPSHEETPAGE**。  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>備註  
 使用此結構來建構後即初始化屬性頁面的外觀。  
  
 如需有關此結構，包括清單的成員，請參閱[PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonapplya--csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 使用者按一下時，會呼叫此成員函式**確定**或**立即套用** 按鈕。  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果所做的變更已被接受。否則為 0。  
  
### <a name="remarks"></a>備註  
 之前`OnApply`可以呼叫架構，您必須先呼叫`SetModified`並將它的參數設定為**TRUE**。 這會啟動**立即套用**按鈕因為使用者在 [屬性] 頁面中進行變更。  
  
 覆寫此成員函式，來指定您的程式會在使用者按一下時的動作**立即套用** 按鈕。 函式覆寫時，應傳回**TRUE**接受變更並**FALSE**以防止變更生效。  
  
 預設實作`OnApply`傳回**TRUE**。  
  
##  <a name="a-nameonhelpa--csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 使用者按一下時，會呼叫此成員函式**協助**屬性頁 按鈕。  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以顯示 [屬性] 頁面上的說明。  
  
##  <a name="a-nameonkillactivea--csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 此成員函式稱為頁面時不會再使用中的頁面。  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料已順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以執行特殊的資料驗證工作。  
  
##  <a name="a-nameonquerycancela--csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 使用者按一下時，會呼叫此成員函式**取消**按鈕，並取消之前採取動作的地方。  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，以允許取消作業。否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以指定程式取得使用者按下時的動作**取消** 按鈕。  
  
 預設實作`OnQueryCancel`傳回**TRUE**。  
  
##  <a name="a-nameonreseta--csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 使用者按一下時，會呼叫此成員函式**取消** 按鈕。  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式時，變更為先前按一下使用者所做的所有屬性頁**立即套用**按鈕會被捨棄，且屬性工作表會保留焦點。  
  
 覆寫此成員函式，來指定程式取得使用者按下時的動作**取消** 按鈕。  
  
##  <a name="a-nameonsetactivea--csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 頁面的使用者會選擇並變成使用中的頁面時，會呼叫此成員函式。  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>傳回值  
 頁面已成功地設使用中; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式時啟動一個頁面時執行工作。 此成員函式的覆寫應該呼叫的預設版本，才進行任何其他處理。  
  
 預設實作會傳回**TRUE**。  
  
##  <a name="a-nameonwizardbacka--csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 使用者按一下時，會呼叫此成員函式**回**在精靈中的按鈕。  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>傳回值  
  
-   0 表示自動前進到前一頁。  
  
-   若要防止變更頁面的-1。  
  
 若要跳至下一個以外的頁面，會傳回要顯示在對話方塊中的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取一些動作**回**按鈕時。  
  
##  <a name="a-nameonwizardfinisha--csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 使用者按一下時，會呼叫此成員函式**完成**在精靈中的按鈕。  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果在精靈完成時，系統會終結屬性工作表否則為零。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取一些動作**完成**按鈕時。  
  
##  <a name="a-nameonwizardnexta--csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 使用者按一下時，會呼叫此成員函式`Next`在精靈中的按鈕。  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>傳回值  
  
-   0 表示自動前進到下一個頁面。  
  
-   若要防止變更頁面的-1。  
  
 若要跳至下一個以外的頁面，會傳回要顯示在對話方塊中的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定使用者必須時採取一些動作`Next`按鈕時。  
  
##  <a name="a-namequerysiblingsa--csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 呼叫此成員函式，來轉送訊息至屬性工作表中的每一頁。  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `wParam`  
 [in]指定訊息相關的其他資訊。  
  
 `lParam`  
 [in]指定訊息相關的其他資訊。  
  
### <a name="return-value"></a>傳回值  
 非零，如果不應該將訊息轉送至下一步 屬性頁。否則為零。  
  
### <a name="remarks"></a>備註  
 如果頁面傳回非零值，屬性工作表不會傳送訊息至後續頁面。  
  
##  <a name="a-namesetmodifieda--csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 若要啟用或停用此成員函式的呼叫**立即套用** 按鈕，根據屬性頁中的設定是否應該套用到適當的外部物件。  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bChanged`  
 [in]**TRUE** ，表示屬性頁設定具有已修改最後一次套用;**FALSE** ，表示屬性頁設定已套用，或應該忽略。  
  
### <a name="remarks"></a>備註  
 屬性工作表會保留的頁面是 「 不正常 」，也就是追蹤、 屬性頁，您已經呼叫**SetModified (TRUE)**。 **立即套用**將永遠會啟用按鈕，如果您呼叫**SetModified (TRUE)**的其中一個頁面。 **立即套用**將停用 按鈕，當您呼叫**SetModified (FALSE)**的其中一個頁面，但如果沒有其他頁面的 「 不正常 」。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

