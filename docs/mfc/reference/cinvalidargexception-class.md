---
title: "CInvalidArgException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException class
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 19
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
ms.openlocfilehash: 4091c0e8a35320482eba193c89c90982c7e4fca9
ms.lasthandoff: 02/24/2017

---
# <a name="cinvalidargexception-class"></a>CInvalidArgException 類別
這個類別表示無效引數例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|建構函式。|  
  
## <a name="remarks"></a>備註  
 A`CInvalidArgException`物件表示無效的引數例外狀況。  
  
 如需有關例外狀況處理的詳細資訊，請參閱[CException 類別](../../mfc/reference/cexception-class.md)主題和[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException  
 建構函式。  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>備註  
 直接; 請勿使用這個建構函式呼叫全域函式**AfxThrowInvalidArgException**。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSimpleException 類別](../../mfc/reference/csimpleexception-class.md)

