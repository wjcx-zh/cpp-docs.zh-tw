---
title: "CDynamicStringAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72ca3d1626b22f286a7e1ca9a276582d68cd7619
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 類別
讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。  
  
## <a name="syntax"></a>語法  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|擷取指定資料行的資料做為字串。|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|設定指定資料行的資料做為字串。|  
  
## <a name="remarks"></a>備註  
 雖然[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)要求提供者，所報告的原生格式資料`CDynamicStringAccessor`要求提供者擷取從資料存放區做為字串資料存取的所有資料。 這是不需要計算值的資料存放區，例如顯示或列印的資料存放區內容的簡單工作特別有用。  
  
 資料存放區中資料行資料的原生類型是什麼並不重要，只要提供者可以支援資料轉換即可，它會以字串格式提供資料。 如果提供者不支援從原生資料類型轉換成字串 （這是不常見），要求的呼叫會傳回成功值**DB_S_ERRORSOCCURED**，並將對應的資料行的狀態指出轉換問題**DBSTATUS_E_CANTCONVERTVALUE**。  
  
 使用`CDynamicStringAccessor`方法，取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。  
  
 資料行資訊會儲存在緩衝區中建立和管理由這個類別。 取得資料緩衝區使用[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)，或將它存放至緩衝區使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)。  
  
 討論和使用動態存取子類別的範例，請參閱[使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。  
  
## <a name="requirements"></a>需求  
 **標頭檔**：atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)