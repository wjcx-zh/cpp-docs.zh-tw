---
title: CDocObjectServerItem 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e660144808c3e9abf8f8c090b9af5ff2eb73d9e9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211801"
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
|[CDocObjectServerItem::GetDocument](#getdocument)|擷取包含項目的文件的指標。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|如果架構嘗試隱藏 DocObject 項目，則會擲回例外狀況。|  
|[CDocObjectServerItem::OnShow](#onshow)|由架構呼叫以讓 DocObject 項目就地使用中。 如果項目不是 DocObject，呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|  
  
## <a name="remarks"></a>備註  
 `CDocObjectServerItem` 定義可覆寫成員函式： [OnHide](#onhide)， [OnOpen](https://msdn.microsoft.com/7a9b1363-6ad8-4732-9959-4e35c07644fd)，並[OnShow](#onshow)。  
  
 若要使用`CDocObjectServerItem`，確保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)覆寫中您`COleServerDoc`-衍生的類別會傳回新`CDocObjectServerItem`物件。 如果您需要變更您的項目中的任何功能，您可以建立您自己的新執行個體`CDocObjectServerItem`-衍生的類別。  
  
 如需 DocObjects 的詳細資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)並[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 參考 》*。 另請參閱[網際網路前幾個步驟： 主動式文件](../../mfc/active-documents-on-the-internet.md)並[主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem  
 建構 `CDocObjectServerItem` 物件。  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>參數  
 *pServerDoc*  
 文件會包含新的 DocObject 項目的指標。  
  
 *bAutoDelete*  
 指出發行它的連結時，是否可以刪除物件。 設定引數為 false`CDocObjectServerItem`物件是您的文件資料中不可或缺的一部分。 請將它設定為 TRUE，如果物件是用來識別架構來刪除您的文件資料中某個範圍的第二個結構。  
  
##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument  
 擷取包含項目的文件的指標。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含項目; 的文件指標如果項目不是文件的一部分，則為 NULL。  
  
### <a name="remarks"></a>備註  
 這可讓您傳遞的引數為伺服器文件存取權[CDocObjectServerItem](#cdocobjectserveritem)建構函式。  
  
##  <a name="onhide"></a>  CDocObjectServerItem::OnHide  
 由架構呼叫以隱藏項目。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>備註  
 如果項目 DocObject，則預設實作會擲回例外狀況。 您無法隱藏現用的 DocObject 項目，因為這會整個檢視。 您必須停用 DocObject 項目，以使其消失。 如果項目不是 DocObject 的預設實作會呼叫[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。  
  
##  <a name="onshow"></a>  CDocObjectServerItem::OnShow  
 由架構呼叫以指示伺服器應用程式做出 DocObject 項目就地使用中。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>備註  
 如果項目不是 DocObject 的預設實作會呼叫[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果您想要執行的特殊處理開啟 DocObject 項目時，請覆寫這個函式。  
  
## <a name="see-also"></a>另請參閱  
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer 類別](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem 類別](../../mfc/reference/coledocobjectitem-class.md)
