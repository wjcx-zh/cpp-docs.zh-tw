---
title: "使用可驗證的組件搭配 SQL Server (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "可驗證的組件 [C++], 使用 SQL Server"
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用可驗證的組件搭配 SQL Server (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

封裝為動態連結程式庫 \(DLL\) 的延伸預存程序，會透過使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 開發的函式來提供擴充的 SQL Server 功能。  延伸預存程序會實作為 DLL 內的函式。  除了函式以外，延伸預存程序還可以定義[使用者定義型別](../cpp/classes-and-structs-cpp.md)和[彙總函式](http://msdn.microsoft.com/zh-tw/de255454-f45e-4281-81f9-bc61893ac5da) \(例如 SUM 和 AVG\)。  
  
 當用戶端執行了延伸預存程序時，SQL Server 會搜尋與延伸預存程序有關的 DLL 並載入 DLL。  SQL Server 會呼叫要求的延伸預存程序，並在指定的安全性內容中執行它。  然後延伸預存程序會傳遞結果集，並將參數傳回至伺服器。  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)] 提供了 Transact\-SQL \(T\-SQL\) 的擴充部分，讓您能把可驗證的組件安裝至 SQL Server。  SQL Server 使用權限集合會以下列的安全性層級來指定安全性內容：  
  
-   不受限制模式：您必須自行承擔執行程式碼的風險，因為程式碼沒有經過型別安全的驗證。  
  
-   安全模式：執行可驗證的型別安全程式碼，使用 \/clr:safe 編譯。  
  
 安全模式要求所執行的組件必須通過型別安全的驗證。  
  
 若要建立可驗證的組件並將它載入 SQL Server，請使用 Transact\-SQL 命令 CREATE ASSEMBLY 和 DROP ASSEMBLY，如下所示：  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 PERMISSION\_SET 命令會指定安全性內容，並可以擁有 UNRESTRICTED、SAFE 或 EXTENDED 值。  
  
 此外，您可以使用 CREATE FUNCTION 命令，繫結至類別中的方法名稱：  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## 範例  
 下列 SQL 指令碼 \(例如，名為 "MyScript.sql"\) 會載入組件至 SQL Server，並且能夠讓您使用類別的方法：  
  
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
  
 SQL 指令碼可以在 SQL Query Analyzer 中以互動的方式執行，或是在命令列搭配 sqlcmd.exe 公用程式使用。  下列命令列會連接至 MyServer、使用預設資料庫和信任的連接、並且輸入 MyScript.sql 和輸出 MyResult.txt。  
  
```  
sqlcmd –S MyServer -E –i myScript.sql –o myResult.txt  
```  
  
## 請參閱  
 [如何：移轉至 \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [類別和結構](../cpp/classes-and-structs-cpp.md)