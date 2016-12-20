---
title: "如何：封送處理 ADO.NET 的 VARIANT (C++/CLI) | Microsoft Docs"
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
  - "ADO.NET [C++], 封送處理 VARIANT 類型"
  - "VARIANT"
  - "VARIANT, 封送處理"
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：封送處理 ADO.NET 的 VARIANT (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

示範如何將原生 `VARIANT` 加入至資料庫中，以及如何將 <xref:System.Object?displayProperty=fullName> 從資料庫封送處理為原生 `VARIANT`。  
  
## 範例  
 在此範例中，會建立類別 DatabaseClass，使其與 ADO.NET <xref:System.Data.DataTable> 物件互動。  請注意，這個類別是原生 C\+\+ `class` \(相較於 `ref class` 或 `value class` 而言\)。  因為要從機器碼使用此類別，而且無法在機器碼中使用 Managed 型別，所以這點是必要的。  如類別宣告之前的 `#pragma managed` 指示詞所表示，這個類別將會編譯成以 CLR 為目標。  如需這個指示詞的詳細資訊，請參閱 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 請注意 DatabaseClass 類別的私用成員：`gcroot<DataTable ^> table`。  由於原生型別不能包含 Managed 型別，所以 `gcroot` 關鍵字是必要的。  如需 `gcroot` 的詳細資訊，請參閱 [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 如同 `main` 之前的 `#pragma unmanaged` 指示詞所表示的，此範例中的其餘程式碼都是原生 C\+\+ 程式碼。  在此範例中，會建立 DatabaseClass 的新執行個體並呼叫它的方法，以建立資料表，並在此資料表中填入一些資料列。  請注意，原生 `VARIANT` 型別會傳遞至資料庫資料行 ObjectCol 做為其值。  在 DatabaseClass 之內，會使用 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空間中可以找到的封送處理功能，將這些 `VARIANT` 型別封送處理為 Managed 物件。  具體而言，<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> 方法是用於將 `VARIANT` 封送處理為 <xref:System.Object>，而 <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> 方法則用於將 <xref:System.Object> 封送處理為 `VARIANT`。  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
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
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
  **ObjectCol: 這是 VARIANT 中的 BSTR。**  
**ObjectCol: 42**   
## 編譯程式碼  
  
-   若要從命令列編譯程式碼，請將程式碼範例儲存於名為 adonet\_marshal\_variant.cpp 的檔案中，並且輸入下列陳述式：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## .NET Framework 安全性  
 如需與 ADO.NET 有關的安全性問題之詳細資訊，請參閱[保護 ADO.NET 應用程式](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices>   
 [資料存取](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-tw/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)