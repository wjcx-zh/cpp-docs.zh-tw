---
title: "如何：封送處理 ADO.NET 的 Unicode 字串 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO.NET [C++], 封送處理 Unicode 字串"
  - "字串 [C++], Unicode"
  - "Unicode [C++], 字串"
ms.assetid: 1da090ff-6b53-40be-841f-dc79dfe8ba10
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：封送處理 ADO.NET 的 Unicode 字串 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

示範如何將原生 Unicode 字串 \(`wchar_t *`\) 加入至資料庫，以及如何從資料庫將 <xref:System.String?displayProperty=fullName> 封送至原生 Unicode 字串。  
  
## 範例  
 在此範例中，會建立類別 DatabaseClass，使其與 ADO.NET <xref:System.Data.DataTable> 物件互動。  請注意，這個類別是原生 C\+\+ `class` \(相較於 `ref class` 或 `value class` 而言\)。  因為要從機器碼使用此類別，而且無法在機器碼中使用 Managed 型別，所以這點是必要的。  如類別宣告之前的 `#pragma managed` 指示詞所表示，這個類別將會編譯成以 CLR 為目標。  如需這個指示詞的詳細資訊，請參閱 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 請注意 DatabaseClass 類別的私用成員：`gcroot<DataTable ^> table`。  由於原生型別不能包含 Managed 型別，所以 `gcroot` 關鍵字是必要的。  如需 `gcroot` 的詳細資訊，請參閱 [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 如同 `main` 之前的 `#pragma unmanaged` 指示詞所表示的，此範例中的其餘程式碼都是原生 C\+\+ 程式碼。  在此範例中，會建立 DatabaseClass 的新執行個體並呼叫它的方法，以建立資料表，並在此資料表中填入一些資料列。  請注意，Unicode C\+\+ 字串會傳遞至資料庫資料行 StringCol 做為其值。  在 DatabaseClass 之內，會使用 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空間中可以找到的封送處理功能，將這些字串封送處理到 Managed 字串。  具體而言，<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 方法是用於將 `wchar_t *` 封送處理為 <xref:System.String>，而 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 方法則用於將 <xref:System.String> 封送處理為 `wchar_t *`。  
  
> [!NOTE]
>  由 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 所配置的記憶體必須透過呼叫 <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> 或 `GlobalFree` 才能取消配置。  
  
```  
// adonet_marshal_string_wide.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(wchar_t *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringUni(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a wchar_t *.  
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(  
                (String ^)rows[i][columnStr]).ToPointer();  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
    db->AddRow(L"This is string 1.");  
    db->AddRow(L"This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    wchar_t *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalUni.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
  **StringCol: 這是字串 1。**  
**StringCol: 這是字串 2。**   
## 編譯程式碼  
  
-   若要從命令列編譯程式碼，請將程式碼範例儲存於名為 adonet\_marshal\_string\_wide.cpp 的檔案中，並且輸入下列陳述式：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  
  
## .NET Framework 安全性  
 如需與 ADO.NET 有關的安全性問題之詳細資訊，請參閱[保護 ADO.NET 應用程式](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices>   
 [資料存取](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-tw/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)