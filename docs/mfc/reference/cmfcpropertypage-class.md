---
title: "CMFCPropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage::PreTranslateMessage method
- CMFCPropertyPage::CreateObject method
- CMFCPropertyPage class
- CMFCPropertyPage::OnSetActive method
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: 30
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0e9cdfa8a98c034839fac119c828cf1b92a1867a
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 類別
`CMFCPropertyPage`類別支援在屬性頁上顯示快顯功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|建構 `CMFCPropertyPage` 物件。|  
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCPropertyPage::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|`CMFCPropertyPage::OnSetActive`|當頁面選擇由使用者變成使用中的頁面，架構會呼叫此成員函式。 (覆寫[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。)|  
|`CMFCPropertyPage::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需詳細資訊和方法語法，請參閱[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CPropertyPage::PreTranslateMessage`。)|  
  
## <a name="remarks"></a>備註  
 `CMFCPropertyPage`類別表示屬性工作表亦稱為標籤對話方塊的個別頁面。  
  
 使用`CMFCPropertyPage`類別搭配[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)類別。 若要使用功能表屬性 頁面上，將所有出現的`CPropertyPage`類別`CMFCPropertyPage`類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpropertypage.h  
  
##  <a name="a-namecmfcpropertypagea--cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage  
 建構 `CMFCPropertyPage` 物件。  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>參數  
 `nIDTemplate`  
 此頁面的範本資源識別碼。  
  
 `nIDCaption`  
 標籤的資源識別碼將在此頁面 索引標籤。 如果為 0，名稱被取自這個網頁的對話方塊範本中。 預設值為 0。  
  
 `lpszTemplateName`  
 此頁面範本的名稱指標。 不能是`NULL`。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如需建構函式參數的詳細資訊，請參閱[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)

