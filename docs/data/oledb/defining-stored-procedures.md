---
title: "定義預存程序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3262396bcaafd1522278d0ac53be5d715966b9d2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="defining-stored-procedures"></a>定義預存程序
然後再呼叫預存程序，您必須先定義，使用[DEFINE_COMMAND](../../data/oledb/define-command.md)巨集。 當您定義命令時，則代表參數以問號 （？） 做為參數標記：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 請注意，本主題中的程式碼範例中使用的語法 （使用大括號和等等的） SQL Server 特定的。 您在預存程序中使用的語法可能會根據您所使用的提供者而有所不同。  
  
 接下來，在參數對應中指定列出的順序出現在命令中的參數，在命令中，使用的參數：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 前一個範例會定義預存程序，因為它會。 一般而言，有效率地重複使用程式碼，如資料庫包含一組預先定義的預存程序名稱，例如 「 銷售年 」 或 「 dt_adduserobject。 」 您可以檢視其定義，使用 SQL Server Enterprise Manager。 如下所示呼叫 (位置的 '？ ' 參數而定，預存程序的介面):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 接下來，請在命令類別宣告：  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 最後，呼叫預存程序中`OpenRowset`，如下所示：  
  
```  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 也請注意，您可以定義預存程序中使用資料庫屬性[db_command](../../windows/db-command.md) ，如下所示：  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)