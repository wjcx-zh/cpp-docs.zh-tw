---
title: "如何： 封送處理 ADO.NET 的 VARIANT (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 504f9553b85acefa085a7a8d6c85768ff934bab7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-a-variant-for-adonet-ccli"></a>如何：封送處理 ADO.NET 的 VARIANT (C++/CLI)
示範如何將原生`VARIANT`到資料庫及如何封送處理<xref:System.Object?displayProperty=fullName>從資料庫為原生`VARIANT`。  
  
## <a name="example"></a>範例  
 在此範例中，必須將類別 DatabaseClass 建立 ADO.NET 與互動<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較之下`ref class`或`value class`)。 這是必要的因為我們想要從原生程式碼，使用此類別，而且您無法在原生程式碼中使用 managed 型別。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 原生類型不能包含 managed 型別，因為`gcroot`是必要的關鍵字。 如需有關`gcroot`，請參閱[How to： 在原生類型中宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 在此範例中的程式碼的其餘部分是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，原生`VARIANT`類型做為值的資料庫資料行 ObjectCol 正在傳遞。 內部 DatabaseClass，這些`VARIANT`類型會封送處理至 managed 物件使用中的封送處理功能<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體而言，此方法<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>用以封送處理`VARIANT`至<xref:System.Object>，和方法<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>用以封送處理<xref:System.Object>至`VARIANT`。  
  
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
  
```Output  
ObjectCol: This is a BSTR in a VARIANT.  
ObjectCol: 42  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要從命令列將程式碼編譯、 adonet_marshal_variant.cpp 檔案中儲存的程式碼範例，並輸入下列陳述式：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 包含 ADO.NET 的安全性問題的資訊，請參閱[保護 ADO.NET 應用程式](/dotnet/framework/data/adonet/securing-ado-net-applications)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.InteropServices>   
 [使用 ADO.NET 資料存取 (C + + /CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [互通性](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)