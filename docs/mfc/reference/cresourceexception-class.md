---
title: "CResourceException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs: C++
helpviewer_keywords: CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 497ced5337a44bb0d72be734cfea35a30ead383b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cresourceexception-class"></a>CResourceException 類別
當 Windows 找不到或無法配置所要求的資源時產生的。  
  
## <a name="syntax"></a>語法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
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
 請勿直接使用這個建構函式，但是而不是呼叫全域函式[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 如需例外狀況的詳細資訊，請參閱文章[在 MFC 中處理例外狀況](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](cexception-class.md)   
 [階層架構圖表](../hierarchy-chart.md)


