---
title: "DAO 資料庫引擎初始化及終止 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 13
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
ms.openlocfilehash: b6119279234558998fad1f220239a29618c69cc5
ms.lasthandoff: 02/24/2017

---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止
使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。  
  
### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|  
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|  
  
##  <a name="a-nameafxdaoinita--afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit  
 此函式會初始化 DAO 資料庫引擎。  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不需要呼叫`AfxDaoInit`因為應用程式會自動呼叫它時需要它。  
  
 如需相關資訊，以及呼叫的範例`AfxDaoInit`，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameafxdaoterma--afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm  
 此函式會終止 DAO 資料庫引擎。  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>備註  
 一般而言，您只需要呼叫此函式中的標準 DLL;應用程式會自動呼叫`AfxDaoTerm`需要時。  
  
 在標準 Dll，呼叫`AfxDaoTerm`之前`ExitInstance`函式，但要等到所有的 MFC DAO 物件已終結之後。  
  
 如需相關資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdao.h  

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

