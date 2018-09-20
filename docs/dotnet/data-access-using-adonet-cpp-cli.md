---
title: 使用 ADO.NET 進行資料存取 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fdb3bdd921c32e14744c9dbfd29690c4b028cc07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384646"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 進行資料存取 (C++/CLI)

ADO.NET 是.NET Framework API 進行資料存取，並提供能力和易用性使用先前的資料存取解決方案不相符。 本章節描述一些問題牽涉到 ADO.NET 所特有 Visual c + + 的使用者，例如封送處理原生類型。

ADO.NET 會執行在 Common Language Runtime (CLR)。 因此，任何與 ADO.NET 互動的應用程式也必須目標 CLR。 不過，這不表示原生應用程式無法使用 ADO.NET。 這些範例將示範如何從原生程式碼 ADO.NET 資料庫互動。

## <a name="marshal_ansi"></a> 封送處理 ADO.NET 的 ANSI 字串

示範如何將原生的字串 (`char *`) 的資料庫，以及如何封送處理至<xref:System.String?displayProperty=fullName>從原生字串至資料庫。

### <a name="example"></a>範例

在此範例中，類別 DatabaseClass 建立互動使用 ADO.NET<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較`ref class`或`value class`)。 這是必要的因為我們想要使用原生程式碼，這個類別，而且您無法在原生程式碼中使用 managed 的類型。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱 < [managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 由於原生類型不能包含 managed 型別，`gcroot`是必要的關鍵字。 如需詳細資訊`gcroot`，請參閱 <<c2> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

在此範例中的程式碼的其餘部分會是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，原生 c + + 字串傳遞做為資料庫資料行將 StringCol 的值。 內 DatabaseClass，這些字串會封送處理為使用中的封送處理功能的 managed 字串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體來說，此方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>用來封送處理`char *`要<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>用以封送處理<xref:System.String>至`char *`。

> [!NOTE]
>  所配置的記憶體<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>必須先將它解除配置，藉由呼叫<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>或`GlobalFree`。

```cpp
// adonet_marshal_string_native.cpp
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

    void AddRow(char *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringAnsi(
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

    int GetValuesForColumn(char *dataColumn, char **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringAnsi(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a char *.
            values[i] = (char *)Marshal::StringToHGlobalAnsi(
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
    db->AddRow("This is string 1.");
    db->AddRow("This is string 2.");

    // Now retrieve the rows and display their contents.
    char *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        "StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        cout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalAnsi.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>編譯程式碼

- 若要編譯的程式碼，從命令列，將程式碼範例儲存在名為 adonet_marshal_string_native.cpp 並輸入下列陳述式：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_bstr"></a> 封送處理 ADO.NET 的 BSTR 字串

示範如何將 COM 字串 (`BSTR`) 的資料庫，以及如何封送處理<xref:System.String?displayProperty=fullName>將資料庫從`BSTR`。

### <a name="example"></a>範例

在此範例中，類別 DatabaseClass 建立互動使用 ADO.NET<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較`ref class`或`value class`)。 這是必要的因為我們想要使用原生程式碼，這個類別，而且您無法在原生程式碼中使用 managed 的類型。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱 < [managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 由於原生類型不能包含 managed 型別，`gcroot`是必要的關鍵字。 如需詳細資訊`gcroot`，請參閱 <<c2> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

在此範例中的程式碼的其餘部分會是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，COM 字串會傳遞做為資料庫資料行將 StringCol 的值。 內 DatabaseClass，這些字串會封送處理為使用中的封送處理功能的 managed 字串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體來說，此方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>用來封送處理`BSTR`要<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>用以封送處理<xref:System.String>至`BSTR`。

> [!NOTE]
>  所配置的記憶體<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>必須先將它解除配置，藉由呼叫<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>或`SysFreeString`。

``` cpp
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

### <a name="compiling-the-code"></a>編譯程式碼

- 若要編譯的程式碼，從命令列，將程式碼範例儲存在名為 adonet_marshal_string_native.cpp 並輸入下列陳述式：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_unicode"></a> 封送處理 ADO.NET 的 Unicode 字串

示範如何將原生的 Unicode 字串 (`wchar_t *`) 的資料庫，以及如何封送處理至<xref:System.String?displayProperty=fullName>從原生的 Unicode 字串的資料庫。

### <a name="example"></a>範例

在此範例中，類別 DatabaseClass 建立互動使用 ADO.NET<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較`ref class`或`value class`)。 這是必要的因為我們想要使用原生程式碼，這個類別，而且您無法在原生程式碼中使用 managed 的類型。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱 < [managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 由於原生類型不能包含 managed 型別，`gcroot`是必要的關鍵字。 如需詳細資訊`gcroot`，請參閱 <<c2> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

在此範例中的程式碼的其餘部分會是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，Unicode c + + 字串傳遞做為資料庫資料行將 StringCol 的值。 內 DatabaseClass，這些字串會封送處理為使用中的封送處理功能的 managed 字串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體來說，此方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>用來封送處理`wchar_t *`要<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>用以封送處理<xref:System.String>至`wchar_t *`。

> [!NOTE]
>  所配置的記憶體<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>必須先將它解除配置，藉由呼叫<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>或`GlobalFree`。

```cpp
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

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>編譯程式碼

- 若要編譯的程式碼，從命令列，將程式碼範例儲存在名為 adonet_marshal_string_wide.cpp 並輸入下列陳述式：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal_variant"></a> 封送處理 ADO.NET 的 VARIANT

示範如何將原生`VARIANT`資料庫，以及如何封送處理<xref:System.Object?displayProperty=fullName>從原生資料庫`VARIANT`。

### <a name="example"></a>範例

在此範例中，類別 DatabaseClass 建立互動使用 ADO.NET<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較`ref class`或`value class`)。 這是必要的因為我們想要使用原生程式碼，這個類別，而且您無法在原生程式碼中使用 managed 的類型。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱 < [managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 由於原生類型不能包含 managed 型別，`gcroot`是必要的關鍵字。 如需詳細資訊`gcroot`，請參閱 <<c2> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

在此範例中的程式碼的其餘部分會是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，原生`VARIANT`類型傳遞做為資料庫資料行將 ObjectCol 的值。 內 DatabaseClass，這些`VARIANT`類型會封送處理至使用中的封送處理功能的 managed 物件<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體來說，此方法<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>用來封送處理`VARIANT`要<xref:System.Object>，和方法<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>用以封送處理<xref:System.Object>至`VARIANT`。

```cpp
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

### <a name="compiling-the-code"></a>編譯程式碼

- 若要編譯的程式碼，從命令列，將程式碼範例儲存在名為 adonet_marshal_variant.cpp 並輸入下列陳述式：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal_safearray"></a> 封送處理 ADO.NET 的 SAFEARRAY

示範如何將原生`SAFEARRAY`資料庫，以及如何封送處理為原生資料庫從 managed 的陣列`SAFEARRAY`。

### <a name="example"></a>範例

在此範例中，類別 DatabaseClass 建立互動使用 ADO.NET<xref:System.Data.DataTable>物件。 請注意，這個類別是原生 c + + `class` (相較`ref class`或`value class`)。 這是必要的因為我們想要使用原生程式碼，這個類別，而且您無法在原生程式碼中使用 managed 的類型。 這個類別將會編譯為 CLR 為目標的會以`#pragma managed`類別宣告之前的指示詞。 如需有關這個指示詞的詳細資訊，請參閱 < [managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table`。 由於原生類型不能包含 managed 型別，`gcroot`是必要的關鍵字。 如需詳細資訊`gcroot`，請參閱 <<c2> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

在此範例中的程式碼的其餘部分會是原生 c + + 程式碼，會以`#pragma unmanaged`指示詞前面`main`。 在此範例中，我們會建立 DatabaseClass 的新執行個體，並呼叫其方法來建立資料表，並填入資料表中的某些資料列。 請注意，原生`SAFEARRAY`類型傳遞做為資料庫資料行將 ArrayIntsCol 的值。 內 DatabaseClass，這些`SAFEARRAY`類型會封送處理至使用中的封送處理功能的 managed 物件<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空間。 具體來說，此方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用來封送處理`SAFEARRAY`整數和方法的 managed 陣列<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用來封送處理 managed 的陣列的整數以`SAFEARRAY`。

```cpp
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

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="compiling-the-code"></a>編譯程式碼

- 若要編譯的程式碼，從命令列，將程式碼範例儲存在名為 adonet_marshal_safearray.cpp 並輸入下列陳述式：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

如需涉及 ADO.NET 的安全性問題的資訊，請參閱[保護 ADO.NET 應用程式](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相關章節

|區段|描述|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|提供 ADO.NET，一組類別公開給.NET 程式設計人員的資料存取服務的概觀。|

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互通性](/dotnet/framework/interop/index)
