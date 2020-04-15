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
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364417"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 進行資料存取 (C++/CLI)

ADO.NET是用於資料存取的 .NET 框架 API,提供前所未有的資料存取解決方案所無法比擬的電源和易用性。 本節介紹一些涉及 Visual C++ 用戶獨有的ADO.NET的問題,例如封送本機類型。

ADO.NET在通用語言運行時 (CLR) 下運行。 因此,任何與ADO.NET交互的應用程式也必須針對CLR。 但是,這並不意味著本機應用程式不能使用ADO.NET。 這些範例將展示如何與來自本機代碼的ADO.NET資料庫進行互動。

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>為ADO.NET的封送 ANSI 字串

展示如何向資料庫添加本機字串 (`char *`) 以及如何<xref:System.String?displayProperty=fullName>將從資料庫封送到本機字串。

### <a name="example"></a>範例

在此範例中,創建類DatabaseClass是為了與ADO.NET<xref:System.Data.DataTable>物件進行互動。 請注意,此類是本機C++(`class`與`ref class``value class`或 相比)。 這是必需的,因為我們希望從本機代碼使用此類,並且不能在本機代碼中使用託管類型。 此類將編譯為針對 CLR,如類聲明前面`#pragma managed`的 指令所示。 有關此指令的詳細資訊,請參閱[託管、非託管](../preprocessor/managed-unmanaged.md)。

請注意資料庫類別的私有成員: `gcroot<DataTable ^> table`。 由於本機類型不能包含託管類型,`gcroot`因此關鍵字是必需的。 有關 的詳細`gcroot`資訊 ,請參閱[:在本機類型中宣告句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代碼的其餘部分是本機C++代碼,如前面的`#pragma unmanaged``main`指令所示。 在此範例中,我們正在創建一個新的DatabaseClass實例,並調用其方法來創建表並填充表中的某些行。 請注意,本機C++字串作為資料庫列StringCol的值傳遞。 在 DatabaseClass 中,這些字串<xref:System.Runtime.InteropServices?displayProperty=fullName>使用 命名空間中的封送功能將封送到託管字串。 具體而言,該方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>用於將`char *`a<xref:System.String>封<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>送 到,<xref:System.String>並且`char *`該方法用於將 a 封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>記憶體必須通過調用<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>`GlobalFree`或進行分配。

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

- 要從命令列編譯代碼,請在名為 adonet_marshal_string_native.cpp 的檔案中儲存代碼範例,並輸入以下語句:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>ADO.NET 的 BSTR 字串

展示如何向資料庫加入 COM 字`BSTR`串 ( ,<xref:System.String?displayProperty=fullName>以及如何將從`BSTR`資料庫封送到 。

### <a name="example"></a>範例

在此範例中,創建類DatabaseClass是為了與ADO.NET<xref:System.Data.DataTable>物件進行互動。 請注意,此類是本機C++(`class`與`ref class``value class`或 相比)。 這是必需的,因為我們希望從本機代碼使用此類,並且不能在本機代碼中使用託管類型。 此類將編譯為針對 CLR,如類聲明前面`#pragma managed`的 指令所示。 有關此指令的詳細資訊,請參閱[託管、非託管](../preprocessor/managed-unmanaged.md)。

請注意資料庫類別的私有成員: `gcroot<DataTable ^> table`。 由於本機類型不能包含託管類型,`gcroot`因此關鍵字是必需的。 有關 的詳細`gcroot`資訊 ,請參閱[:在本機類型中宣告句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代碼的其餘部分是本機C++代碼,如前面的`#pragma unmanaged``main`指令所示。 在此範例中,我們正在創建一個新的DatabaseClass實例,並調用其方法來創建表並填充表中的某些行。 請注意,COM 字串作為資料庫列 StringCol 的值傳遞。 在 DatabaseClass 中,這些字串<xref:System.Runtime.InteropServices?displayProperty=fullName>使用 命名空間中的封送功能將封送到託管字串。 具體而言,該方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>用於將`BSTR`a<xref:System.String>封<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>送 到,<xref:System.String>並且`BSTR`該方法用於將 a 封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>記憶體必須通過調用<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>`SysFreeString`或進行分配。

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

- 要從命令列編譯代碼,請在名為 adonet_marshal_string_native.cpp 的檔案中儲存代碼範例,並輸入以下語句:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>為ADO.NET而封送 Unicode 字串

展示如何將本機 Unicode 字串`wchar_t *`( ) 加入到資料庫<xref:System.String?displayProperty=fullName>以及如何將 從資料庫封送到本機 Unicode 字串。

### <a name="example"></a>範例

在此範例中,創建類DatabaseClass是為了與ADO.NET<xref:System.Data.DataTable>物件進行互動。 請注意,此類是本機C++(`class`與`ref class``value class`或 相比)。 這是必需的,因為我們希望從本機代碼使用此類,並且不能在本機代碼中使用託管類型。 此類將編譯為針對 CLR,如類聲明前面`#pragma managed`的 指令所示。 有關此指令的詳細資訊,請參閱[託管、非託管](../preprocessor/managed-unmanaged.md)。

請注意資料庫類別的私有成員: `gcroot<DataTable ^> table`。 由於本機類型不能包含託管類型,`gcroot`因此關鍵字是必需的。 有關 的詳細`gcroot`資訊 ,請參閱[:在本機類型中宣告句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代碼的其餘部分是本機C++代碼,如前面的`#pragma unmanaged``main`指令所示。 在此範例中,我們正在創建一個新的DatabaseClass實例,並調用其方法來創建表並填充表中的某些行。 請注意,Unicode C++字串作為資料庫列 StringCol 的值傳遞。 在 DatabaseClass 中,這些字串<xref:System.Runtime.InteropServices?displayProperty=fullName>使用 命名空間中的封送功能將封送到託管字串。 具體而言,該方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>用於將`wchar_t *`a<xref:System.String>封<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>送 到,<xref:System.String>並且`wchar_t *`該方法用於將 a 封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>記憶體必須通過調用<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>`GlobalFree`或進行分配。

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

- 要從命令列編譯代碼,請在名為 adonet_marshal_string_wide.cpp 的檔案中儲存代碼範例,並輸入以下語句:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>為ADO.NET編送一個 VARIANT

展示如何將本機`VARIANT`新增到資料庫以及如何將<xref:System.Object?displayProperty=fullName>從資料庫封送到`VARIANT`本機 。

### <a name="example"></a>範例

在此範例中,創建類DatabaseClass是為了與ADO.NET<xref:System.Data.DataTable>物件進行互動。 請注意,此類是本機C++(`class`與`ref class``value class`或 相比)。 這是必需的,因為我們希望從本機代碼使用此類,並且不能在本機代碼中使用託管類型。 此類將編譯為針對 CLR,如類聲明前面`#pragma managed`的 指令所示。 有關此指令的詳細資訊,請參閱[託管、非託管](../preprocessor/managed-unmanaged.md)。

請注意資料庫類別的私有成員: `gcroot<DataTable ^> table`。 由於本機類型不能包含託管類型,`gcroot`因此關鍵字是必需的。 有關 的詳細`gcroot`資訊 ,請參閱[:在本機類型中宣告句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代碼的其餘部分是本機C++代碼,如前面的`#pragma unmanaged``main`指令所示。 在此範例中,我們正在創建一個新的DatabaseClass實例,並調用其方法來創建表並填充表中的某些行。 請注意,本機`VARIANT`類型作為資料庫列 ObjectCol 的值傳遞。 在 DatabaseClass`VARIANT`中<xref:System.Runtime.InteropServices?displayProperty=fullName>,使用 命名空間中的封送功能將這些類型的封送到託管物件。 具體而言,該方法<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>用於將`VARIANT`a<xref:System.Object>封<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>送 到 ,<xref:System.Object>`VARIANT`並且該方法用於將 .

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

- 要從命令列編譯代碼,請在名為 adonet_marshal_variant.cpp 的檔案中儲存代碼範例,並輸入以下語句:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>為ADO.NET封送 SAFEARRAY

展示如何將本機`SAFEARRAY`新增到資料庫以及如何將託管陣列從資料庫封送到本機`SAFEARRAY`。

### <a name="example"></a>範例

在此範例中,創建類DatabaseClass是為了與ADO.NET<xref:System.Data.DataTable>物件進行互動。 請注意,此類是本機C++(`class`與`ref class``value class`或 相比)。 這是必需的,因為我們希望從本機代碼使用此類,並且不能在本機代碼中使用託管類型。 此類將編譯為針對 CLR,如類聲明前面`#pragma managed`的 指令所示。 有關此指令的詳細資訊,請參閱[託管、非託管](../preprocessor/managed-unmanaged.md)。

請注意資料庫類別的私有成員: `gcroot<DataTable ^> table`。 由於本機類型不能包含託管類型,`gcroot`因此關鍵字是必需的。 有關 的詳細`gcroot`資訊 ,請參閱[:在本機類型中宣告句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代碼的其餘部分是本機C++代碼,如前面的`#pragma unmanaged``main`指令所示。 在此範例中,我們正在創建一個新的DatabaseClass實例,並調用其方法來創建表並填充表中的某些行。 請注意,本機`SAFEARRAY`類型作為資料庫列 ArrayIntsCol 的值傳遞。 在 DatabaseClass`SAFEARRAY`中<xref:System.Runtime.InteropServices?displayProperty=fullName>,使用 命名空間中的封送功能將這些類型的封送到託管物件。 具體而言,該方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用於將`SAFEARRAY`a 整理到由整數組成的託管陣列,<xref:System.Runtime.InteropServices.Marshal.Copy%2A>該方法 用於將管理整數陣列`SAFEARRAY`封送到 。

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

- 要從命令列編譯代碼,請在名為 adonet_marshal_safearray.cpp 的檔案中儲存代碼範例,並輸入以下語句:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

有關涉及ADO.NET的安全問題的資訊,請參閱[保護ADO.NET應用程式](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相關章節

|區段|描述|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|提供ADO.NET的概述,這是一組向 .NET 程式師公開數據訪問服務的類。|

## <a name="see-also"></a>另請參閱

[.NET 程式設計,帶C++/CLI(視覺C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[本機與 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互通性](/dotnet/framework/interop/index)
