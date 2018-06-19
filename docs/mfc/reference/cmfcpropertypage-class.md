---
title: CMFCPropertyPage 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3352841b1b495d1718ffa6be034239ecd7e50c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366638"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 類別
`CMFCPropertyPage`類別支援在屬性頁上顯示快顯功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|建構 `CMFCPropertyPage` 物件。|  
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCPropertyPage::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|`CMFCPropertyPage::OnSetActive`|此成員函式是由架構呼叫，當頁面由使用者選擇，並會變成使用中的頁面。 (覆寫[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。)|  
|`CMFCPropertyPage::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需詳細資訊和方法語法，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CPropertyPage::PreTranslateMessage`。)|  
  
## <a name="remarks"></a>備註  
 `CMFCPropertyPage`類別表示屬性工作表，亦稱為索引標籤對話方塊的個別頁面。  
  
 使用`CMFCPropertyPage`類別搭配[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)類別。 若要在屬性頁上，使用功能表，取代所有出現之`CPropertyPage`類別`CMFCPropertyPage`類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage  
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
 此頁面的範本資源 ID。  
  
 `nIDCaption`  
 資源識別碼的標籤放置在此頁面 索引標籤。 如果為 0，名稱被取自此頁面的對話方塊範本中。 預設值為 0。  
  
 `lpszTemplateName`  
 此頁面的範本名稱點。 不能`NULL`。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如需建構函式參數的詳細資訊，請參閱[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)
