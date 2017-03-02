---
title: "CUserException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [C++], stopping
- exceptions, throwing
- CUserException class
- errors [C++], trapping
- operations [C++]
- throwing exceptions, stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8548ffa7ad9032e174d650e210a70a29b0e3f19d
ms.lasthandoff: 02/24/2017

---
# <a name="cuserexception-class"></a>CUserException 類別
擲回以停止使用者作業。  
  
## <a name="syntax"></a>語法  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>備註  
 使用`CUserException`當您想要用於應用程式特定的例外狀況擲回/catch 例外狀況機制。 「 使用者 」 中的類別名稱可以解譯為 「 我的使用者進行某項操作，需要處理例外狀況。 」  
  
 A`CUserException`通常會呼叫全域函式之後擲回`AfxMessageBox`來通知使用者作業已失敗。 當您撰寫例外狀況處理常式時，處理例外狀況，特別因為使用者通常已經已經被通知失敗。 架構會在某些情況下，擲回這個例外狀況。 擲回`CUserException`自己，警告使用者，並接著呼叫全域函式`AfxThrowUserException`。  
  
 在下列範例中，包含可能會失敗的作業的函式會警示使用者並擲回`CUserException`。 呼叫函式攔截到例外狀況，並特別處理它︰  
  
 [!code-cpp[NVC_MFCExceptions #&24;](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 如需有關使用`CUserException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)

