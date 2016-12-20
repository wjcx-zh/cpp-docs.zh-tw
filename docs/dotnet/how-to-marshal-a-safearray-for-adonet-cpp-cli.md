---
title: "如何：封送處理 ADO.NET 的 SAFEARRAY (C++/CLI) | Microsoft Docs"
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
  - "ADO.NET [C++], 封送處理 SAFEARRAY 類型"
  - "SAFEARRAY, 封送處理"
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：封送處理 ADO.NET 的 SAFEARRAY (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節將示範如何在資料庫中加入原生 `SAFEARRAY`，以及如何將資料庫中的 Managed 陣列封送處理至原生 `SAFEARRAY`。  
  
## 範例  
 在此範例中，會建立類別 DatabaseClass，使其與 ADO.NET <xref:System.Data.DataTable> 物件互動。  請注意，這個類別是原生 C\+\+ `class` \(相較於 `ref class` 或 `value class` 而言\)。  因為要從機器碼使用此類別，而且無法在機器碼中使用 Managed 型別，所以這點是必要的。  如類別宣告之前的 `#pragma managed` 指示詞所表示，這個類別將會編譯成以 CLR 為目標。  如需這個指示詞的詳細資訊，請參閱 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 請注意 DatabaseClass 類別的私用成員：`gcroot<DataTable ^> table`。  由於原生型別不能包含 Managed 型別，所以 `gcroot` 關鍵字是必要的。  如需 `gcroot` 的詳細資訊，請參閱 [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 如同 `main` 之前的 `#pragma unmanaged` 指示詞所表示的，此範例中的其餘程式碼都是原生 C\+\+ 程式碼。  在此範例中，會建立 DatabaseClass 的新執行個體並呼叫它的方法，以建立資料表，並在此資料表中填入一些資料列。  請注意，原生 `SAFEARRAY` 型別是當做資料庫資料行 ArrayIntsCol 的值傳遞。  在 DatabaseClass 內，會使用在 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空間中找到的封送處理 \(Marshaling\) 功能，將這些 `SAFEARRAY` 型別封送處理至 Managed 物件。  明確地說，<xref:System.Runtime.InteropServices.Marshal.Copy%2A> 方法是用來將 `SAFEARRAY` 封送處理至 Managed 整數陣列，而 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 方法則是用來將 Managed 整數陣列封送處理至 `SAFEARRAY`。  
  
```  
// adonet_marshal_safearray.cpp  
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
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
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
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
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
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
## 編譯程式碼  
  
-   若要從命令列編譯程式碼，請將程式碼範例儲存在名稱為 adonet\_marshal\_safearray.cpp 的檔案中，然後輸入下列陳述式 \(Statement\)：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## .NET Framework 安全性  
 如需與 ADO.NET 有關的安全性問題之詳細資訊，請參閱[保護 ADO.NET 應用程式](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices>   
 [資料存取](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-tw/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)