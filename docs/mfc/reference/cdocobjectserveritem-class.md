---
title: "CDocObjectServerItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServerItem class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
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
ms.openlocfilehash: 06cf873512fbf43b729d9a70f185582a4e48cafc
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 類別
實作 DocObject 伺服器專屬的 OLE 伺服器動詞命令。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|建構 `CDocObjectServerItem` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|擷取包含此項目的文件的指標。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|如果架構嘗試隱藏 DocObject 項目，則會擲回例外狀況。|  
|[CDocObjectServerItem::OnShow](#onshow)|呼叫架構，以便讓 DocObject 項目就地使用中。 如果項目不是 DocObject，會呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|  
  
## <a name="remarks"></a>備註  
 `CDocObjectServerItem`定義可覆寫成員函式︰ [OnHide](#onhide)， [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd)，和[OnShow](#onshow)。  
  
 若要使用`CDocObjectServerItem`，確保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中覆寫您`COleServerDoc`-衍生的類別會傳回新`CDocObjectServerItem`物件。 如果您需要變更您的項目中的任何功能，您可以建立您自己的新執行個體`CDocObjectServerItem`-衍生的類別。  
  
 如需 DocObjects 詳細資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 參考*。 另請參閱[網際網路第一個步驟︰ 主動式文件](../../mfc/active-documents-on-the-internet.md)和[主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdocob.h  
  
##  <a name="a-namecdocobjectserveritema--cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem  
 建構 `CDocObjectServerItem` 物件。  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>參數  
 `pServerDoc`  
 文件會包含新的 DocObject 項目的指標。  
  
 `bAutoDelete`  
 表示在發行的連結時，是否可以刪除物件。 引數設定為**FALSE**如果`CDocObjectServerItem`物件是不可或缺的一部分文件的資料。 將它設定為**TRUE**如果物件是用來識別文件的資料可以刪除架構中某個範圍的第二個結構。  
  
##  <a name="a-namegetdocumenta--cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument  
 擷取包含此項目的文件的指標。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向文件，其中包含項目;**NULL**如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 這樣可允許存取做為引數傳遞給您的伺服器文件[CDocObjectServerItem](#cdocobjectserveritem)建構函式。  
  
##  <a name="a-nameonhidea--cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide  
 隱藏項目架構呼叫。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>備註  
 如果項目 DocObject 的預設實作會擲回例外狀況。 您無法隱藏作用中的 DocObject 項目，因為它會接受整個檢視。 您必須停用的 DocObject 項目，使它消失。 如果項目不是 DocObject，預設實作會呼叫[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。  
  
##  <a name="a-nameonshowa--cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow  
 呼叫架構，以便指示伺服器應用程式做出 DocObject 項目就地使用中。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>備註  
 如果項目不是 DocObject，預設實作會呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果您想要執行特殊處理開啟 DocObject 項目時，覆寫這個函式。  
  
## <a name="see-also"></a>另請參閱  
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer 類別](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem 類別](../../mfc/reference/coledocobjectitem-class.md)

