---
title: DAO 資料庫引擎初始化及終止 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f28c0c166bcbf13181161d6afce484fe4a45b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止
使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。  
  
### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|  
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|  
  
##  <a name="afxdaoinit"></a>  AfxDaoInit  
 此函式會初始化 DAO 資料庫引擎。  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不需要呼叫`AfxDaoInit`因為應用程式會自動呼叫它會在需要時。  
  
 如需相關資訊，以及呼叫的範例`AfxDaoInit`，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="afxdaoterm"></a>  AfxDaoTerm  
 此函式會終止 DAO 資料庫引擎。  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>備註  
 一般而言，您只需要在一般 MFC 的 DLL; 呼叫此函式應用程式會自動呼叫`AfxDaoTerm`需要時。  
  
 標準的 MFC Dll 中呼叫`AfxDaoTerm`之前`ExitInstance`函式，但之後所有 MFC DAO 物件已被都終結。  
  
 如需相關資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdao.h  

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
