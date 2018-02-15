---
title: "CDataSource 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b738909197bee9c6fb617da0d10ce09fbd27fd29
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cdatasource-class"></a>CDataSource 類別
對應至 OLE DB 資料來源物件，其表示透過提供者與資料來源的連線。  
  
## <a name="syntax"></a>語法

```cpp
class CDataSource  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/cdatasource-close.md)|關閉連線。|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|擷取目前開啟之資料來源的初始化字串。|  
|[GetProperties](../../data/oledb/cdatasource-getproperties.md)|取得目前針對所連線之資料來源設定的屬性值。|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|取得目前針對所連線資料來源設定的單一屬性值。|  
|[開啟](../../data/oledb/cdatasource-open.md)|建立提供者 （資料來源） 的連接使用**CLSID**， **ProgID**，或`CEnumerator`呼叫端提供的 moniker。|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|從以使用者提供的檔名指定的檔案，開啟資料來源。|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|開啟以初始化字串指定的資料來源。|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|允許使用者選取先前建立的資料連結檔案，以開啟對應的資料來源。|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|使用 [資料連結] 對話方塊開啟資料來源物件。|  
  
## <a name="remarks"></a>備註  
 可為單一連線建立一個或多個資料庫工作階段。 這些工作階段是以 `CSession` 表示。 您必須呼叫[cdatasource:: Open](../../data/oledb/cdatasource-open.md)開啟之前建立的工作階段連線`CSession::Open`。  
  
 如需如何使用的範例`CDataSource`，請參閱[CatDB](../../visual-cpp-samples.md)範例。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)