---
title: "CRichEditDoc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
dev_langs: C++
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c427dc034a37bf3b0686b0fd95e62c3b718fbaea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 類別
與[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供豐富的編輯控制項的 MFC 的文件檢視架構內容中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CRichEditDoc : public COleServerDoc  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](#createclientitem)|呼叫以執行文件的清除作業。|  
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指出資料流輸入和輸出是否應包含格式資訊。|  
|[CRichEditDoc::GetView](#getview)|擷取有關聯[CRichEditView](../../mfc/reference/cricheditview-class.md)物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[Cricheditdoc:: M_brtf](#m_brtf)|指出資料流 I/O 是否應包含格式設定。|  
  
## <a name="remarks"></a>備註  
 「 Rich edit 控制項 」 是一個視窗，使用者可以輸入和編輯文字。 文字字元和段落格式，可以指派，而且可包含內嵌的 OLE 物件。 Rich edit 控制項來格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。  
  
 `CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護檢視表中的用戶端項目的清單。 `CRichEditCntrItem`提供存取權 OLE 用戶端項目給容器端。  
  
 這個 Windows 通用控制項 (因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用於在 Windows 95/98、 Windows NT 的版本 3.51 下執行的程式和更新版本。  
  
 在 MFC 應用程式中使用豐富的編輯文件的範例，請參閱[WORDPAD](../../visual-cpp-samples.md)範例應用程式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrich.h  
  
##  <a name="createclientitem"></a>CRichEditDoc::CreateClientItem  
 呼叫此函式可建立`CRichEditCntrItem`物件，並將它加入至這份文件。  
  
```  
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;  
```  
  
### <a name="parameters"></a>參數  
 *preo*  
 指標[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)結構描述 OLE 項目。 新`CRichEditCntrItem`物件會建構包含這個 OLE 項目。 如果*preo*是**NULL**，新的用戶端項目是空的。  
  
### <a name="return-value"></a>傳回值  
 新的指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件已加入至這份文件。  
  
### <a name="remarks"></a>備註  
 此函式不會執行任何 OLE 初始化。  
  
 如需詳細資訊，請參閱[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) Windows SDK 中的結構。  
  
##  <a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat  
 呼叫此函式可判斷文字格式進行串流的豐富的編輯內容。  
  
```  
int GetStreamFormat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下列旗標其中一項：  
  
- `SF_TEXT`表示 rich edit 控制項不會維護格式資訊。  
  
- `SF_RTF`表示 rich edit 控制項沒有維護格式資訊。  
  
### <a name="remarks"></a>備註  
 傳回值根據[m_bRTF](#m_brtf)資料成員。 此函數會傳回`SF_RTF`如果`m_bRTF`是**TRUE**，否則`SF_TEXT`。  
  
##  <a name="getview"></a>CRichEditDoc::GetView  
 呼叫此函式可存取[CRichEditView](../../mfc/reference/cricheditview-class.md)與此相關聯的物件`CRichEditDoc`物件。  
  
```  
virtual CRichEditView* GetView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CRichEditView`文件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 文字與格式設定資訊都包含在`CRichEditView`物件。 `CRichEditDoc`物件會維護序列化的 OLE 項目。 應該只有一個`CRichEditView`每個`CRichEditDoc`。  
  
##  <a name="m_brtf"></a>Cricheditdoc:: M_brtf  
 當**TRUE**，表示[CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)應該儲存段落和字元格式的特性。  
  
```  
BOOL m_bRTF;  
```  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 WORDPAD](../../visual-cpp-samples.md)   
 [COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument 類別](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl 類別](../../mfc/reference/cricheditctrl-class.md)
