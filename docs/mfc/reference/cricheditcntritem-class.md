---
title: "CRichEditCntrItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem class
- OLE items, in rich edit views
- rich edit controls, using
- rich edit controls, OLE items
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
caps.latest.revision: 24
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
ms.openlocfilehash: b29c7c3b80d24ef9ddb94e09c6b5c7bf2444bb4f
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 類別
使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，提供 rich edit 控制項的 MFC 的文件檢視架構內容中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|建構 `CRichEditCntrItem` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|啟動為其他類型的項目。|  
  
## <a name="remarks"></a>備註  
 「 Rich edit 控制項 」 是一個視窗，讓使用者輸入及編輯文字。 文字字元和段落格式，可以指派，而且可以包含內嵌的 OLE 物件。 Rich edit 控制項來格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。  
  
 `CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`會維護檢視中的 OLE 用戶端項目清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。  
  
 這個 Windows 通用控制項 (並因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 下執行的程式和更新版本。  
  
 在 MFC 應用程式中使用豐富的編輯容器項目，例如，請參閱[WORDPAD](../../visual-cpp-samples.md)範例應用程式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrich.h  
  
##  <a name="a-namecricheditcntritema--cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem  
 呼叫此函式建立`CRichEditCntrItem`物件，並將它加入至容器文件。  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>參數  
 *preo*  
 指標[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)結構描述的 OLE 項目。 新`CRichEditCntrItem`物件會建構包含此 OLE 項目。 如果*preo*是**NULL**，用戶端項目是空的。  
  
 `pContainer`  
 容器文件會包含此項目的指標。 如果`pContainer`是**NULL**，您必須明確地呼叫[COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem)將此用戶端項目加入至文件。  
  
### <a name="remarks"></a>備註  
 此函式不會執行任何 OLE 初始化。  
  
 如需詳細資訊，請參閱[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesynctoricheditobjecta--cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject  
 呼叫此函式來同步處理裝置長寬[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，這個**CRichEditCntrltem**所指定的*reo*。  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>參數  
 *reo*  
 若要參考[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)結構描述的 OLE 項目。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 WORDPAD](../../visual-cpp-samples.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)

