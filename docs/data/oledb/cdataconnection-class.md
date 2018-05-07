---
title: CDataConnection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 945fed5edd59da93aabb1d22e4830417fc4a2518
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnection-class"></a>CDataConnection 類別
管理與資料來源的連線。  
  
## <a name="syntax"></a>語法

```cpp
class CDataConnection  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|建構函式。 執行個體化並初始化`CDataConnection`物件。|  
|[複製](../../data/oledb/cdataconnection-copy.md)|建立現有的資料連接的複本。|  
|[開啟](../../data/oledb/cdataconnection-open.md)|開啟使用初始化字串的資料來源的連接。|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|開啟新的工作階段上目前的連接。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 BOOL](../../data/oledb/cdataconnection-operator-bool.md)|判斷目前的工作階段是否為開啟。|  
|[operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|判斷目前的工作階段是否為開啟。|  
|[CDataSource 運算子 （& s)](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|將參考傳回給包含`CDataSource`物件。|  
|[運算子 CDataSource *](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|將指標傳回至包含的 `CDataSource` 物件。|  
|[運算子 Csession& （& s)](../../data/oledb/cdataconnection-operator-csession-amp.md)|將參考傳回給包含`CSession`物件。|  
|[運算子 CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)|將指標傳回至包含的 `CSession` 物件。|  
  
## <a name="remarks"></a>備註  
 `CDataConnection` 是有用的類別來建立用戶端，因為它封裝所需的物件 （資料來源和工作階段） 和一些您需要連接到資料來源時執行  
  
 不含`CDataConnection`，您必須建立`CDataSource`物件，呼叫其[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)方法，然後建立的執行個體[CSession](../../data/oledb/csession-class.md)物件，呼叫其[開啟](../../data/oledb/csession-open.md)方法，然後建立[CCommand](../../data/oledb/ccommand-class.md)物件並呼叫其**開啟*** 方法。  
  
 與`CDataConnection`，您只需要建立連線物件，請將它傳遞初始字串，然後使用該連接開啟的命令。 如果您打算重複使用資料庫的連接，則最好讓連線保持開啟，並`CDataConnection`提供便利的方式執行此作業。  
  
> [!NOTE]
>  如果您要建立需要處理多個工作階段的資料庫應用程式，您必須使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)