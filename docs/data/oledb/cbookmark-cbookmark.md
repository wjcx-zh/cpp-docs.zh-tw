---
title: 'Cbookmark:: Cbookmark |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7663c34fc9eea5f4262fea6b347c1b7899ace85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095231"
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
  
## <a name="see-also"></a>另請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)