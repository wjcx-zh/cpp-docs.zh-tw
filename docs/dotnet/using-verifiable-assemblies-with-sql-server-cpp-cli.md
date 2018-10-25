---
title: 使用可驗證的組件搭配 SQL Server (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 109b0303eaf4c4352d4e9b426642f92e361051a4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063402"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>使用可驗證的組件搭配 SQL Server (C++/CLI)

擴充預存程序，封裝成動態連結程式庫 (Dll)，可用來擴充 SQL Server 功能，透過使用 Visual c + + 開發的函式。 擴充預存程序會實作為 Dll 內的函式。 除了函數以外，擴充預存程序也可以定義[使用者定義型別](../cpp/classes-and-structs-cpp.md)和彙總函式 （例如，SUM 或 AVG）。

當用戶端執行擴充預存程序時，SQL Server dll 的搜尋與擴充預存程序相關聯，並載入 DLL。 SQL Server 會呼叫要求的擴充預存程序，並在指定的安全性內容下執行它。 擴充預存程序，然後將結果集，並傳回至伺服器的參數。

SQL Server transact-sql (T-SQL) 可讓您可驗證的組件安裝到 SQL Server 提供延伸模組。 SQL Server 權限集合指定的安全性內容，含有下列層級的安全性：

- 不受限制的模式： 自行承擔風險; 來執行程式碼程式碼可能沒有可驗證的型別安全。

- 安全模式： 執行可驗證的型別安全程式碼。使用 /clr: safe 編譯。

> [!IMPORTANT]
> 已被取代的 visual Studio 2015 和 Visual Studio 2017 不支援 **/clr: pure**並 **/clr: safe**建立可驗證的專案。 如果您需要可驗證程式碼，我們建議您將轉譯成 C# 程式碼。

建立和可驗證的組件載入到 SQL Server，請使用 CREATE ASSEMBLY 和 DROP ASSEMBLY TRANSACT-SQL 命令，如下所示：

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

PERMISSION_SET 命令指定的安全性內容中，並可以有不受限制、 保險箱或擴充的值。

此外，您可以使用 CREATE FUNCTION 命令繫結至類別中的方法名稱：

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>範例

下列 SQL 指令碼 (比方說，具名"MyScript.sql 」) 將組件載入至 SQL Server，並提供類別的方法：

```sql
-- Create assembly without external access
drop assembly stockNoEA
go
create assembly stockNoEA
from
'c:\stockNoEA.dll'
with permission_set safe

-- Create function on assembly with no external access
drop function GetQuoteNoEA
go
create function GetQuoteNoEA(@sym nvarchar(10))
returns real
external name stockNoEA:StockQuotes::GetQuote
go

-- To call the function
select dbo.GetQuoteNoEA('MSFT')
go
```

可以以互動方式執行 SQL 指令碼，在 SQL Query Analyzer 或 sqlcmd.exe 公用程式命令列。 下列命令列連接到 MyServer，使用預設的資料庫、 使用信任的連接，輸入 MyScript.sql 及輸出 MyResult.txt。

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)