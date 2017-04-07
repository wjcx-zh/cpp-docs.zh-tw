---
title: "CResourceException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- resource allocation exception
- resources [C++], allocating
- resource exceptions
- exceptions, resource
- CResourceException class
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2013a73f91687277df9dd1e6747aba2dd02a4346
ms.lasthandoff: 02/24/2017

---
# <a name="cresourceexception-class"></a>CResourceException 類別
當 Windows 找不到或無法配置所要求的資源時產生的。  
  
## <a name="syntax"></a>語法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|建構 `CResourceException` 物件。|  
  
## <a name="remarks"></a>備註  
 沒有進一步限定性條件是必要或不可能。  
  
 如需有關使用`CResourceException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cresourceexception"></a>CResourceException::CResourceException  
 建構 `CResourceException` 物件。  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>備註  
 請勿直接使用這個建構函式，但呼叫全域函式，而是[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 如需例外狀況的詳細資訊，請參閱文章[在 MFC 中處理例外狀況](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](cexception-class.md)   
 [階層架構圖表](../hierarchy-chart.md)



