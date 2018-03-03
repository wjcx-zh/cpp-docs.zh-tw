---
title: "CUserException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4613f2ba06ffa697df219172b98a5cf193c1f3b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cuserexception-class"></a>CUserException 類別
擲回以停止使用者作業。  
  
## <a name="syntax"></a>語法  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>備註  
 使用`CUserException`當您想要用於應用程式特定的例外狀況擲回/catch 例外狀況機制。 「 使用者 」 類別名稱中的可以解譯為 「 我的使用者沒有例外狀況，需要處理的項目。 」  
  
 A`CUserException`通常會呼叫全域函式之後擲回`AfxMessageBox`通知作業失敗的使用者。 當您撰寫例外狀況處理常式時，請特別因為使用者通常已經已通知失敗的處理例外狀況。 架構會在某些情況下，擲回這個例外狀況。 擲回`CUserException`自己，警示使用者，然後呼叫全域函式`AfxThrowUserException`。  
  
 在下列範例中，包含可能會失敗的作業的函式會提醒使用者，並擲回`CUserException`。 呼叫的函式攔截例外狀況並加以處理，特別：  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 如需有關使用`CUserException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)
