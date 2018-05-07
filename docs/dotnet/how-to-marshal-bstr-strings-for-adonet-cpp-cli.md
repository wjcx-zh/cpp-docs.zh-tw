---
title: 如何： 封送處理 ADO.NET 的 BSTR 字串 (C + + /CLI) |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
ms.assetid: 5daf4d9e-6ae8-4604-908f-855e37c8d636
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 633b9d623a759caaee3aa6dcf2c93d95549927d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-bstr-strings-for-adonet-ccli"></a>如何：封送處理 ADO.NET 的 BSTR 字串 (C++/CLI)
示範如何將 COM 字串 (`BSTR`) 到資料庫及如何封送處理<xref:System.String?displayProperty=fullName>將資料庫從`BSTR`。  
  
## <a name="example"></a>範例  
 在此範例中，必須將類別 DatabaseClass 建立 ADO.NET 與互動<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較之下`ref class`或`value class`)。 這是必要的因為我們想要從原生程式碼，使用此類別，而且您無法在原生程式碼中使用 managed 型別。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 原生類型不能包含 managed 型別，因為`gcroot`是必要的關鍵字。 如需有關`gcroot`，請參閱[How to： 在原生類型中宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 在此範例中的程式碼的其餘部分是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，正在傳遞做為值的資料庫資料行 StringCol COM 字串。 內部 DatabaseClass，這些字串會封送處理為使用中的封送處理功能的 managed 字串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體而言，此方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>用以封送處理`BSTR`至<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>用以封送處理<xref:System.String>至`BSTR`。  
  
> [!NOTE]
>  所配置的記憶體<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>必須藉由呼叫取消配置<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>或`SysFreeString`。  
  
```  
// adonet_marshal_string_bstr.cpp  
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
  
    void AddRow(BSTR stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringBSTR(  
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
  
    int GetValuesForColumn(BSTR dataColumn, BSTR *values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringBSTR(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a BSTR.  
            values[i] = (BSTR)Marshal::StringToBSTR(  
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
  
    BSTR str1 = SysAllocString(L"This is string 1.");  
    db->AddRow(str1);  
  
    BSTR str2 = SysAllocString(L"This is string 2.");  
    db->AddRow(str2);  
  
    // Now retrieve the rows and display their contents.  
    BSTR values[MAXCOLS];  
    BSTR str3 = SysAllocString(L"StringCol");  
    int len = db->GetValuesForColumn(  
        str3, values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToBSTR.  
        SysFreeString(values[i]);  
    }  
  
    SysFreeString(str1);  
    SysFreeString(str2);  
    SysFreeString(str3);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要從命令列將程式碼編譯、 adonet_marshal_string_native.cpp 檔案中儲存的程式碼範例，並輸入下列陳述式：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 包含 ADO.NET 的安全性問題的資訊，請參閱[保護 ADO.NET 應用程式](/dotnet/framework/data/adonet/securing-ado-net-applications)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices>   
 [使用 ADO.NET 資料存取 (C + + /CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [互通性](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)