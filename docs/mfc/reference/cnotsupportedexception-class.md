---
title: CNotSupportedException 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 510f9db4a7e5688df76baafa868846fd1614f584
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 類別
表示因要求不支援的功能而產生的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|建構 `CNotSupportedException` 物件。|  
  
## <a name="remarks"></a>備註  
 沒有進一步限定性條件是必要或不可能。  
  
 如需有關使用`CNotSupportedException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException  
 建構 `CNotSupportedException` 物件。  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>備註  
 請勿直接使用這個建構函式，但是而不是呼叫全域函式[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)。 如需例外狀況處理的詳細資訊，請參閱文章[在 MFC 中處理例外狀況](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](cexception-class.md)   
 [階層架構圖表](../hierarchy-chart.md)


