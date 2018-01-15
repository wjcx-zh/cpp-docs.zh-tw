---
title: "CDocItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs: C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a4987554965674612eaf8d9aa78c659f7f28b75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdocitem-class"></a>CDocItem 類別
文件項目的基底類別，這些項目是文件資料的元件。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|傳回包含之項目的文件。|  
|[CDocItem::IsBlank](#isblank)|判斷項目是否包含任何資訊。|  
  
## <a name="remarks"></a>備註  
 `CDocItem`物件可用來代表用戶端和伺服器文件中的 OLE 項目。  
  
 如需詳細資訊，請參閱文章[容器： 實作容器](../../mfc/containers-implementing-a-container.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="getdocument"></a>CDocItem::GetDocument  
 呼叫此函式可取得包含項目的文件。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向文件，其中包含項目。**NULL**，如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 此函式在衍生類別中覆寫[COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)，傳回的指標為[COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)物件。  
  
##  <a name="isblank"></a>CDocItem::IsBlank  
 預設的序列化發生時由架構呼叫。  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果項目不包含任何資訊。否則便是 0。  
  
### <a name="remarks"></a>備註  
 根據預設，`CDocItem`物件不是空白。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)物件有時候是空白因為它們直接衍生自`CDocItem`。 不過， [COleServerItem](../../mfc/reference/coleserveritem-class.md)物件永遠為空白。 根據預設，OLE 應用程式包含`COleClientItem`物件沒有 x 或 y 範圍會序列化。 這是藉由傳回**TRUE**的覆寫從`IsBlank`項目時有任何 x 或 y 範圍。  
  
 如果您想要在序列化期間實作其他動作，請覆寫這個函式。  
  
## <a name="see-also"></a>請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDocument 類別](../../mfc/reference/coledocument-class.md)   
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)
