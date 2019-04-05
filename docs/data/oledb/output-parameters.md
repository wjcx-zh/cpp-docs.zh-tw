---
title: 輸出參數
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: 196c50ea62c3e3188b61a3b35a9e2752740c4ad5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027450"
---
# <a name="output-parameters"></a>輸出參數

呼叫預存程序是類似於執行 SQL 命令。 主要差異是預存程序使用輸出參數 （或 「 outparameters"），並傳回值。

下列預存程序，第一個 '？ '的傳回值 (phone) 和第二個是'？ ' 是輸入的參數 （名稱）：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

您可以指定 in 和 out 參數在參數對應：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

您的應用程式必須處理從預存程序所傳回的輸出。 不同的 OLE DB 提供者傳回輸出參數，並傳回結果處理期間的不同時間的值。 比方說，Microsoft OLE DB provider for SQL Server (SQLOLEDB) 不提供輸出參數和傳回碼，直到取用者已經擷取或取消預存程序所傳回的結果集之後。 從伺服器傳回的最後一個 TDS 封包的輸出。

## <a name="row-count"></a>資料列計數

如果您執行具有 outparameters 的預存程序使用 OLE DB 消費者樣板，直到您關閉資料列集，未設定的資料列計數。

例如，請考慮使用資料列集和具預存程序：

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount`具報告測試資料表中傳回多少資料列。 不過，此預存程序會限制為 50 的資料列數目。 例如，如果在測試中有 100 個資料列，資料列計數會是 50 （因為這段程式碼會擷取前 50 個資料列）。 如果有先前只有 30 個資料列的資料表中，資料列計數會是 30。 請務必呼叫`Close`或`CloseAll`填入具之前擷取其值。

## <a name="see-also"></a>另請參閱

[使用預存程序](../../data/oledb/using-stored-procedures.md)