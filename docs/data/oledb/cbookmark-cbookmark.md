---
title: CBookmark::CBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd3529272031e779afdc5315d90613867dcbb823
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
建構函式。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CBookmark();   

CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>參數  
 `nSize`  
 [in] 書籤緩衝區的大小 (以位元組為單位)。  
  
## <a name="remarks"></a>備註  
 第一個函式會將緩衝區設定為**NULL**和緩衝區大小為 0。 第二個函式會將緩衝區大小設定為 `nSize`，將緩衝區設定為 `nSize` 位元組的位元組陣列。  
  
> [!NOTE]
>  此函式僅供以**CBookmark\<0 >**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)