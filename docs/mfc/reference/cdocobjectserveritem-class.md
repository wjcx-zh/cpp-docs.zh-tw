---
title: "CDocObjectServerItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs: C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7627fbc7cb5d36bd82e130264d2653d5a8464545
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 類別
實作 DocObject 伺服器專屬的 OLE 伺服器動詞命令。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|建構 `CDocObjectServerItem` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|擷取包含之項目的文件的指標。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|如果架構嘗試隱藏 DocObject 項目，就會擲回例外狀況。|  
|[CDocObjectServerItem::OnShow](#onshow)|由架構呼叫以讓 DocObject 項目就地使用中。 如果未 DocObject 項目，會呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|  
  
## <a name="remarks"></a>備註  
 `CDocObjectServerItem`定義可覆寫成員函式： [OnHide](#onhide)， [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd)，和[OnShow](#onshow)。  
  
 若要使用`CDocObjectServerItem`，確保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中覆寫您`COleServerDoc`-衍生的類別會傳回新`CDocObjectServerItem`物件。 如果您需要變更您的項目中的任何功能，您可以建立您自己的新執行個體`CDocObjectServerItem`-衍生的類別。  
  
 如需 DocObjects 的進一步資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 參考*。 另請參閱[網際網路第一個步驟： 主動式文件](../../mfc/active-documents-on-the-internet.md)和[主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem  
 建構 `CDocObjectServerItem` 物件。  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>參數  
 `pServerDoc`  
 文件會包含新 DocObject 項目的指標。  
  
 `bAutoDelete`  
 指示發行的連結時，是否可以刪除物件。 將引數設**FALSE**如果`CDocObjectServerItem`物件是不可或缺的一部分文件的資料。 將它設定為**TRUE**如果物件是用來識別文件的資料可以刪除架構中的範圍的第二個結構。  
  
##  <a name="getdocument"></a>CDocObjectServerItem::GetDocument  
 擷取包含之項目的文件的指標。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向文件，其中包含項目。**NULL**如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 這可讓您傳遞的引數為伺服器文件的存取[CDocObjectServerItem](#cdocobjectserveritem)建構函式。  
  
##  <a name="onhide"></a>CDocObjectServerItem::OnHide  
 由架構呼叫以隱藏項目。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>備註  
 如果項目 DocObject 預設實作會擲回例外狀況。 您無法隱藏 active DocObject 項目，因為它會接受整個檢視。 您必須停用 DocObject 項目，使它消失。 如果項目不是 DocObject 的預設實作會呼叫[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。  
  
##  <a name="onshow"></a>CDocObjectServerItem::OnShow  
 由架構呼叫以指示伺服器應用程式進行 DocObject 項目就地使用中。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>備註  
 如果項目不是 DocObject 的預設實作會呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果您想要執行特殊處理開啟 DocObject 項目時，請覆寫這個函式。  
  
## <a name="see-also"></a>請參閱  
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer 類別](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem 類別](../../mfc/reference/coledocobjectitem-class.md)
