---
title: 'Cdynamicaccessor:: Setblobhandling |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ee2c2d57f9f413346bb33a178fc3d8fa90439e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
設定 BLOB 處理目前的資料列的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
      bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>參數  
 `eBlobHandling`  
 指定 BLOB 資料的處理方式。 它可以接受下列值：  
  
-   **DBBLOBHANDLING_DEFAULT**： 處理資料行資料的大小多於`nBlobSize`(為設定由`SetBlobSizeLimit`) 做為 BLOB 資料，並擷取它透過`ISequentialStream`或`IStream`物件。 此選項將嘗試繫結每個資料行，內含資料的大小多於`nBlobSize`或列為**DBTYPE_IUNKNOWN**作為 BLOB 資料。  
  
-   **DBBLOBHANDLING_NOSTREAMS**： 處理資料行資料的大小多於`nBlobSize`(為設定由`SetBlobSizeLimit`) 做為 BLOB 資料，並擷取它透過提供者配置，取用者所擁有的記憶體中的參考。 此選項適用於具有一個以上的 BLOB 資料行的資料表，以及提供者僅支援一個`ISequentialStream`每個存取子的物件。  
  
-   **DBBLOBHANDLING_SKIP**： 略過 （請不要繫結） 限定為包含 Blob 的資料行 （存取子不可以繫結或擷取資料行值，但它仍會擷取資料行的狀態和長度）。  
  
## <a name="remarks"></a>備註  
 您應該呼叫`SetBlobHandling`之前先呼叫**開啟**。  
  
 建構函式方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)設定處理值的 BLOB **DBBLOBHANDLING_DEFAULT**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)