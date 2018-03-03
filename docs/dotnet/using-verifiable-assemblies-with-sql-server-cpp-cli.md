---
title: "使用可驗證的組件搭配 SQL Server (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d03d54dd52f95f3fbba35bb896594e90aa92e867
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>使用可驗證的組件搭配 SQL Server (C++/CLI)
擴充預存程序，封裝成動態連結程式庫 (Dll)，提供方法來擴充 SQL Server 功能，透過使用 Visual c + + 開發的函式。 擴充預存程序會實作為 Dll 內的函式。 除了函數以外，擴充預存程序也可以定義[使用者定義型別](../cpp/classes-and-structs-cpp.md)和[彙總函式](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da)（例如，SUM 或 AVG）。  
  
 當用戶端執行擴充預存程序時，SQL Server DLL 的搜尋與擴充預存程序相關聯，並將 DLL 載入。 SQL Server 呼叫要求的擴充預存程序，並在指定的安全性內容下執行。 擴充預存程序則會傳遞結果集，並傳回參數傳回給伺服器。  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)]提供 TRANSACT-SQL (T-SQL) 可讓您可驗證的組件安裝到 SQL Server 擴充功能。 SQL Server 權限集合指定的安全性內容，下列層級的安全性：  
  
-   不受限制的模式： 執行程式碼自行承擔;程式碼沒有可驗證的類型安全。  
  
-   安全模式： 執行可驗證的型別安全程式碼。使用 /clr: safe 編譯。  
  
 安全模式需要執行的組件是可驗證的型別安全。  
  
 建立和可驗證的組件載入 SQL Server，請使用 CREATE ASSEMBLY 和卸除組件的 TRANSACT-SQL 命令，如下所示：  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 PERMISSION_SET 命令指定的安全性內容，並可以有不受限制、 安全或延伸的值。  
  
 此外，您可以使用 CREATE FUNCTION 命令將繫結至類別中的方法名稱：  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>範例  
 下列 SQL 指令碼 (例如，具名"MyScript.sql 」) 會將組件載入 SQL Server，並提供類別的方法：  
  
```  
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
  
 在 SQL Query Analyzer 或在命令列使用 sqlcmd.exe 公用程式，可以以互動方式執行 SQL 指令碼。 下列命令列連接到 MyServer、 使用的預設資料庫、 使用信任的連接、 輸入 MyScript.sql，並將輸出 MyResult.txt。  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>請參閱  
 [如何： 移轉至 /clr: safe (C + + /CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [類別和結構](../cpp/classes-and-structs-cpp.md)