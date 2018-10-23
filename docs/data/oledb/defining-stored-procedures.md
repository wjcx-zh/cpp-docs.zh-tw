---
title: 定義預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 769f2bf2c0ef6c2c92b4c0468569e91d399cea59
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808442"
---
# <a name="defining-stored-procedures"></a>定義預存程序

然後再呼叫預存程序，您必須先定義，使用[DEFINE_COMMAND](../../data/oledb/define-command.md)巨集。 當您定義的命令時，表示參數加上問號 （？） 作為參數標記：  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
本主題中的程式碼範例中所使用的語法 （使用大括號，依此類推） 是 SQL Server 特有的。 您在您的預存程序中使用的語法可能會根據您所使用的提供者而有所不同。  
  
接下來，在參數對應中指定的參數清單出現在命令中的順序中的參數，在命令中，使用：  
  
```cpp  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
前一個範例會定義預存程序，因為它會。 一般而言，有效率的重複使用的程式碼時，資料庫包含一組預先定義的預存程序名稱，例如 「 銷售的年份 」 或是 「 dt_adduserobject。 」 您可以檢視其使用 SQL Server Enterprise Manager 中的定義。 如下所示呼叫 (位置的 '？ ' 參數取決於預存程序介面):  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
接下來，請在命令類別宣告：  
  
```cpp  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
最後，呼叫預存程序`OpenRowset`，如下所示：  
  
```cpp  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
也請注意，您可以定義預存程序中使用的資料庫屬性[db_command](../../windows/db-command.md) ，如下所示：  
  
```cpp  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>另請參閱  

[使用預存程序](../../data/oledb/using-stored-procedures.md)