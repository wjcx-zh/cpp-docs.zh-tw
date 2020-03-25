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
ms.openlocfilehash: ece626eb7fbecae9b90321ccc2569607897cf520
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209855"
---
# <a name="output-parameters"></a>輸出參數

呼叫預存程式類似于執行 SQL 命令。 主要差異在於預存程式會使用輸出參數（或 "outparameters"）和傳回值。

在下列預存程式中，第一個 '？ ' 是傳回值（phone），而第二個 '？ ' 是輸入參數（名稱）：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

您可以在參數對應中指定 in 和 out 參數：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

您的應用程式必須處理從預存程式傳回的輸出。 不同的 OLE DB 提供者在結果處理期間，會在不同時間傳回輸出參數和傳回值。 例如，Microsoft OLE DB provider for SQL Server （SQLOLEDB）在取用者已抓取或取消預存程式傳回的結果集之前，不會提供輸出參數和傳回碼。 輸出會從伺服器傳回最後一個 TDS 封包。

## <a name="row-count"></a>資料列計數

如果您使用 OLE DB 取用者範本來執行具有 outparameters 的預存程式，則在您關閉資料列集之前，不會設定資料列計數。

例如，假設有一個具有資料列集和 outparameter 的預存程式：

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount` outparameter 會報告從測試資料表傳回的資料列數目。 不過，這個預存程式會將資料列的數目限制為50。 例如，如果測試中有100個數據列，則 rowcount 會是50（因為此程式碼只會抓取前50個數據列）。 如果資料表中只有30個數據列，則 rowcount 會是30。 在提取其值之前，請務必呼叫 `Close` 或 `CloseAll` 以填入 outparameter。

## <a name="see-also"></a>另請參閱

[使用預存程序](../../data/oledb/using-stored-procedures.md)
