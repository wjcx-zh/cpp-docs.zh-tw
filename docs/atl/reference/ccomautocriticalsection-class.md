---
title: "CComAutoCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d12abfceeebeb1cac89b510c14d7a9211173406e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 類別
`CComAutoCriticalSection`提供方法來取得和釋放重要區段物件的擁有權。  
  
## <a name="syntax"></a>語法  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|建構函式。|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|解構函式。|  
  
## <a name="remarks"></a>備註  
 `CComAutoCriticalSection`類似於類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除了`CComAutoCriticalSection`自動初始化關鍵區段中的物件建構函式。  
  
 通常，您會使用`CComAutoCriticalSection`透過`typedef`名稱[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 此名稱參考`CComAutoCriticalSection`時[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

  
 `Init`和`Term`方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)可用時不使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection  
 建構函式。  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>備註  
 呼叫 Win32 函式[InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472)，其中初始化關鍵區段的物件。  
  
##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 解構函式。  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式呼叫[DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552)，其中關鍵區段物件所使用的系統資源全部釋出。  
  
## <a name="see-also"></a>請參閱  
 [CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)
