---
title: "CMultiPageDHtmlDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog class
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c00af20731b2c47a0074366722da3f4a0711ef85
ms.lasthandoff: 02/24/2017

---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog 類別
多頁對話方塊會循序顯示多個 HTML 網頁並處理來自每頁的事件。  
  
## <a name="syntax"></a>語法  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|建構多頁 （精靈樣式） DHTML 對話方塊物件。|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|終結多頁 DHTML 對話方塊物件。|  
  
## <a name="remarks"></a>備註  
 這樣的機制是[DHTML 和 URL 事件對應](http://msdn.microsoft.com/en-us/2a7332f0-79d7-46e4-b816-0a618c46777a)，其中包含[內嵌事件對應](http://msdn.microsoft.com/library/5346210f-f8b7-4e28-9d2c-d9d7fd42421d)針對每個頁面。  
  
## <a name="example"></a>範例  
 此多頁對話方塊假設定義簡單的精靈式功能的三個 HTML 資源。 第一頁`Next`按鈕，第二個**Prev**和`Next`第三個按鈕， **Prev**按鈕。 按下其中一個按鈕時，處理常式函式呼叫[CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)載入適當的新頁面。  
  
 類別中的宣告 （CMyMultiPageDlg.h) 關聯的部分︰  
  
 [!code-cpp[NVC_MFCDocView&181;](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 類別中的實作 （CMyMultipageDlg.cpp) 關聯的部分︰  
  
 [!code-cpp[NVC_MFCDocView #&182;](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdhtml.h  
  
##  <a name="a-namecmultipagedhtmldialoga--cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 建構多頁 （精靈樣式） DHTML 對話方塊物件。  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 對話方塊範本資源的名稱以 null 結束字串。  
  
 `szHtmlResID`  
 以 null 結束的字串是 HTML 資源名稱。  
  
 `pParentWnd`  
 父系或擁有者的視窗物件的指標 (類型的[CWnd](../../mfc/reference/cwnd-class.md)) 對話方塊物件所屬。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的 ID 編號。  
  
 `nHtmlResID`  
 包含 HTML 資源的 ID 編號。  
  
##  <a name="a-namedtorcmultipagedhtmldialoga--cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 終結多頁 DHTML 對話方塊物件。  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>另請參閱  
 [CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)

