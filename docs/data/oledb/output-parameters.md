---
title: "輸出參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 061766f73b554895f8d7ad8952dc6172fd381169
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="output-parameters"></a>輸出參數
呼叫預存程序是類似於叫用 SQL 命令。 主要差異在於預存程序使用輸出參數 （或 「 outparameters"） 和傳回值。  
  
 下列預存程序，第一個 '？ '是傳回的值 (phone)，而第二個'？ ' 是輸入的參數 （名稱）：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 您可以在參數對應中指定 in 和 out 參數：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 您的應用程式必須處理從預存程序傳回的輸出。 不同的 OLE DB 提供者傳回輸出參數和傳回值在結果處理期間的不同時間。 比方說，Microsoft OLE DB provider for SQL Server (SQLOLEDB) 不會不提供輸出參數和傳回碼之前，取用者已經擷取或取消預存程序所傳回的結果集之後。 從伺服器傳回的最後一個 TDS 封包的輸出。  
  
## <a name="row-count"></a>資料列計數  
 如果您要執行的預存程序具有 outparameters 使用 OLE DB 消費者樣板，直到您關閉資料列集未設定的資料列計數。  
  
 例如，請考慮使用資料列集和具預存程序：  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @_rowcount具報告測試資料表實際上未傳回資料列數目。 不過，此預存程序最多 50 個資料列數目限制。 例如，如果測試中有 100 個資料列，資料列計數會是 50 （因為這段程式碼會擷取前 50 資料列）。 如果資料表中只是有 30 個資料列，資料列計數就是 30。 您必須呼叫**關閉**或**CloseAll**填入具之前擷取其值。  
  
## <a name="see-also"></a>請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)