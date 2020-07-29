---
title: 使用 ADO.NET 進行資料存取 (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 3f3980c98890382e77d9d89db2944bebf7b12319
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211056"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 進行資料存取 (C++/CLI)

ADO.NET 是資料存取所需的 .NET Framework API，可讓先前的資料存取解決方案更容易使用並不相符。 本節說明 Visual C++ 使用者特有的 ADO.NET，例如封送處理原生類型的一些問題。

ADO.NET 會在 Common Language Runtime （CLR）下執行。 因此，與 ADO.NET 互動的任何應用程式也必須將目標設為 CLR。 不過，這並不表示原生應用程式無法使用 ADO.NET。 這些範例將示範如何從機器碼與 ADO.NET 資料庫互動。

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>封送處理 ADO.NET 的 ANSI 字串

示範如何將原生字串（ `char *` ）加入至資料庫，以及如何將資料庫的封送處理 <xref:System.String?displayProperty=fullName> 至原生字串。

### <a name="example"></a>範例

在此範例中，會建立類別 DatabaseClass 來與 ADO.NET 物件互動 <xref:System.Data.DataTable> 。 請注意，這個類別是原生 c + + **`class`** （相較于 **`ref class`** 或 **`value class`** ）。 這是必要的，因為我們想要從機器碼使用這個類別，而且您無法在機器碼中使用 managed 類型。 這個類別會編譯成以 CLR 為目標，如同在類別宣告前面的指示詞所表示 `#pragma managed` 。 如需此指示詞的詳細資訊，請參閱[managed、非受控](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table` 。 由於原生類型不能包含 managed 類型，因此 `gcroot` 必須要有關鍵詞。 如需的詳細資訊 `gcroot` ，請參閱[如何：在原生類型中宣告控制碼](../dotnet/how-to-declare-handles-in-native-types.md)。

本範例中的其餘程式碼是原生 c + + 程式碼，如前面的指示詞所表示 `#pragma unmanaged` `main` 。 在此範例中，我們會建立 DatabaseClass 的新實例，並呼叫其方法來建立資料表，並在資料表中填入部分資料列。 請注意，原生 c + + 字串會當做資料庫資料行 StringCol 的值來傳遞。 在 DatabaseClass 內，這些字串會使用命名空間中找到的封送處理功能封送處理至 managed 字串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具體而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> 是用來將封送處理 `char *` 至 <xref:System.String> ，而方法 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 則是用來將封送處理 <xref:System.String> 至 `char *` 。

> [!NOTE]
> 所配置的記憶體 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 必須藉由呼叫或解除 <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> 分配 `GlobalFree` 。

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

- 若要從命令列編譯器代碼，請將程式碼範例儲存在名為 adonet_marshal_string_native 的檔案中，然後輸入下列語句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>封送處理 ADO.NET 的 BSTR 字串

示範如何將 COM 字串（）加入 `BSTR` 至資料庫，以及如何將資料庫的封送處理 <xref:System.String?displayProperty=fullName> 至 `BSTR` 。

### <a name="example"></a>範例

在此範例中，會建立類別 DatabaseClass 來與 ADO.NET 物件互動 <xref:System.Data.DataTable> 。 請注意，這個類別是原生 c + + **`class`** （相較于 **`ref class`** 或 **`value class`** ）。 這是必要的，因為我們想要從機器碼使用這個類別，而且您無法在機器碼中使用 managed 類型。 這個類別會編譯成以 CLR 為目標，如同在類別宣告前面的指示詞所表示 `#pragma managed` 。 如需此指示詞的詳細資訊，請參閱[managed、非受控](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table` 。 由於原生類型不能包含 managed 類型，因此 `gcroot` 必須要有關鍵詞。 如需的詳細資訊 `gcroot` ，請參閱[如何：在原生類型中宣告控制碼](../dotnet/how-to-declare-handles-in-native-types.md)。

本範例中的其餘程式碼是原生 c + + 程式碼，如前面的指示詞所表示 `#pragma unmanaged` `main` 。 在此範例中，我們會建立 DatabaseClass 的新實例，並呼叫其方法來建立資料表，並在資料表中填入部分資料列。 請注意，COM 字串會當做資料庫資料行 StringCol 的值來傳遞。 在 DatabaseClass 內，這些字串會使用命名空間中找到的封送處理功能封送處理至 managed 字串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具體而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 是用來將封送處理 `BSTR` 至 <xref:System.String> ，而方法 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 則是用來將封送處理 <xref:System.String> 至 `BSTR` 。

> [!NOTE]
> 所配置的記憶體 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 必須藉由呼叫或解除 <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> 分配 `SysFreeString` 。

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

- 若要從命令列編譯器代碼，請將程式碼範例儲存在名為 adonet_marshal_string_native 的檔案中，然後輸入下列語句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>封送處理 ADO.NET 的 Unicode 字串

示範如何將原生 Unicode 字串（ `wchar_t *` ）加入至資料庫，以及如何將資料庫的封送處理 <xref:System.String?displayProperty=fullName> 至原生 unicode 字串。

### <a name="example"></a>範例

在此範例中，會建立類別 DatabaseClass 來與 ADO.NET 物件互動 <xref:System.Data.DataTable> 。 請注意，這個類別是原生 c + + **`class`** （相較于 **`ref class`** 或 **`value class`** ）。 這是必要的，因為我們想要從機器碼使用這個類別，而且您無法在機器碼中使用 managed 類型。 這個類別會編譯成以 CLR 為目標，如同在類別宣告前面的指示詞所表示 `#pragma managed` 。 如需此指示詞的詳細資訊，請參閱[managed、非受控](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table` 。 由於原生類型不能包含 managed 類型，因此 `gcroot` 必須要有關鍵詞。 如需的詳細資訊 `gcroot` ，請參閱[如何：在原生類型中宣告控制碼](../dotnet/how-to-declare-handles-in-native-types.md)。

本範例中的其餘程式碼是原生 c + + 程式碼，如前面的指示詞所表示 `#pragma unmanaged` `main` 。 在此範例中，我們會建立 DatabaseClass 的新實例，並呼叫其方法來建立資料表，並在資料表中填入部分資料列。 請注意，Unicode c + + 字串會當做資料庫資料行 StringCol 的值傳遞。 在 DatabaseClass 內，這些字串會使用命名空間中找到的封送處理功能封送處理至 managed 字串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具體而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 是用來將封送處理 `wchar_t *` 至 <xref:System.String> ，而方法 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 則是用來將封送處理 <xref:System.String> 至 `wchar_t *` 。

> [!NOTE]
> 所配置的記憶體 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 必須藉由呼叫或解除 <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> 分配 `GlobalFree` 。

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

- 若要從命令列編譯器代碼，請將程式碼範例儲存在名為 adonet_marshal_string_wide 的檔案中，然後輸入下列語句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>封送處理 ADO.NET 的 VARIANT

示範如何將原生新增 `VARIANT` 至資料庫，以及如何將資料庫的封送處理 <xref:System.Object?displayProperty=fullName> 至原生 `VARIANT` 。

### <a name="example"></a>範例

在此範例中，會建立類別 DatabaseClass 來與 ADO.NET 物件互動 <xref:System.Data.DataTable> 。 請注意，這個類別是原生 c + + **`class`** （相較于 **`ref class`** 或 **`value class`** ）。 這是必要的，因為我們想要從機器碼使用這個類別，而且您無法在機器碼中使用 managed 類型。 這個類別會編譯成以 CLR 為目標，如同在類別宣告前面的指示詞所表示 `#pragma managed` 。 如需此指示詞的詳細資訊，請參閱[managed、非受控](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table` 。 由於原生類型不能包含 managed 類型，因此 `gcroot` 必須要有關鍵詞。 如需的詳細資訊 `gcroot` ，請參閱[如何：在原生類型中宣告控制碼](../dotnet/how-to-declare-handles-in-native-types.md)。

本範例中的其餘程式碼是原生 c + + 程式碼，如前面的指示詞所表示 `#pragma unmanaged` `main` 。 在此範例中，我們會建立 DatabaseClass 的新實例，並呼叫其方法來建立資料表，並在資料表中填入部分資料列。 請注意，原生 `VARIANT` 類型會當做資料庫資料行 ObjectCol 的值來傳遞。 在 DatabaseClass 內， `VARIANT` 會使用命名空間中的封送處理功能，將這些類型封送處理至 managed 物件 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具體而言，方法 <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> 是用來將封送處理 `VARIANT` 至 <xref:System.Object> ，而方法 <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> 則是用來將封送處理 <xref:System.Object> 至 `VARIANT` 。

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

- 若要從命令列編譯器代碼，請將程式碼範例儲存在名為 adonet_marshal_variant 的檔案中，然後輸入下列語句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>封送處理 ADO.NET 的 SAFEARRAY

示範如何將原生新增 `SAFEARRAY` 至資料庫，以及如何將 managed 陣列從資料庫封送處理至原生 `SAFEARRAY` 。

### <a name="example"></a>範例

在此範例中，會建立類別 DatabaseClass 來與 ADO.NET 物件互動 <xref:System.Data.DataTable> 。 請注意，這個類別是原生 c + + **`class`** （相較于 **`ref class`** 或 **`value class`** ）。 這是必要的，因為我們想要從機器碼使用這個類別，而且您無法在機器碼中使用 managed 類型。 這個類別會編譯成以 CLR 為目標，如同在類別宣告前面的指示詞所表示 `#pragma managed` 。 如需此指示詞的詳細資訊，請參閱[managed、非受控](../preprocessor/managed-unmanaged.md)。

請注意 DatabaseClass 類別的私用成員： `gcroot<DataTable ^> table` 。 由於原生類型不能包含 managed 類型，因此 `gcroot` 必須要有關鍵詞。 如需的詳細資訊 `gcroot` ，請參閱[如何：在原生類型中宣告控制碼](../dotnet/how-to-declare-handles-in-native-types.md)。

本範例中的其餘程式碼是原生 c + + 程式碼，如前面的指示詞所表示 `#pragma unmanaged` `main` 。 在此範例中，我們會建立 DatabaseClass 的新實例，並呼叫其方法來建立資料表，並在資料表中填入部分資料列。 請注意，原生 `SAFEARRAY` 類型會當做資料庫資料行 ArrayIntsCol 的值來傳遞。 在 DatabaseClass 內， `SAFEARRAY` 會使用命名空間中的封送處理功能，將這些類型封送處理至 managed 物件 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具體而言，方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 是用來將封送處理 `SAFEARRAY` 至整數的 managed 陣列，而方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 則是用來將整數的 managed 陣列封送處理至 `SAFEARRAY` 。

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

- 若要從命令列編譯器代碼，請將程式碼範例儲存在名為 adonet_marshal_safearray 的檔案中，然後輸入下列語句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

如需有關 ADO.NET 的安全性問題的資訊，請參閱[保護 ADO.NET 應用程式](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相關章節

|區段|描述|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|提供 ADO.NET 的總覽，這是將資料存取服務公開給 .NET 程式設計人員的一組類別。|

## <a name="see-also"></a>另請參閱

[使用 c + +/CLI 進行 .NET 程式設計（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互通性](/dotnet/framework/interop/index)
