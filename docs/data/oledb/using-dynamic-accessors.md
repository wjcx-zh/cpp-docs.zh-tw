---
title: 使用動態存取子
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4539247894c3980464e744c76cea450324372382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649718"
---
# <a name="using-dynamic-accessors"></a>使用動態存取子

動態存取子可讓您存取資料來源，當您有不了解資料庫結構描述 （基礎結構）。 OLE DB 樣板程式庫提供數個類別，可協助您。

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)範例示範如何使用動態存取子類別來取得資料行資訊，並以動態方式建立存取子。

## <a name="using-cdynamicaccessor"></a>使用 CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)可讓您存取資料來源，當您有不了解資料庫結構描述 （資料庫的基礎結構）。 `CDynamicAccessor` 方法會取得資料行名稱、 計數等資料類型的資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。 資料行資訊會儲存在緩衝區中，建立和管理由這個類別。 取得從緩衝區使用的資料[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)方法。

## <a name="example"></a>範例

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>使用 CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)運作方式類似[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，除非有一個重要的差異。 雖然`CDynamicAccessor`要求的資料提供者，報告的原生格式`CDynamicStringAccessor`要求提供者擷取從資料存放區做為字串資料存取的所有資料。 此程序是特別適合不需要計算值的資料存放區，例如顯示或列印的資料存放區內容的簡單工作項目。

使用`CDynamicStringAccessor`方法，以取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。 資料行資訊會儲存在緩衝區中由這個類別建立和管理。 取得從緩衝區使用的資料[cdynamicstringaccessor:: Getstring](../../data/oledb/cdynamicstringaccessor-getstring.md)或將它儲存至緩衝區使用[cdynamicstringaccessor:: Setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)。

## <a name="example"></a>範例

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>使用 CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)大致[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，只不過`CDynamicParameterAccessor`取得要設定呼叫的參數資訊[ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)介面。 提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。

參數資訊會儲存在這個類別建立和管理的緩衝區中。 從緩衝區取得參數資料，使用[cdynamicparameteraccessor:: Getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md)並[cdynamicparameteraccessor:: Getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)。

如需示範如何使用這個類別來執行 SQL Server 預存程序，並取得輸出參數值的範例，請參閱[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)中的程式碼範例[Microsoft： 位](https://github.com/Microsoft/VCSamples)在 GitHub 上的存放庫。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
