---
title: 使用動態存取子
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: eea1c6199fed5a4e6e331c1c76f34b96090b709a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509416"
---
# <a name="using-dynamic-accessors"></a>使用動態存取子

當您不知道 (基礎結構) 的資料庫架構時，動態存取子可讓您存取資料來源。 OLE DB 範本程式庫提供數個類別來協助您。

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)範例顯示如何使用動態存取子類別來取得資料行資訊，以及動態建立存取子。

## <a name="using-cdynamicaccessor"></a>使用 CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 可讓您在資料庫的基礎結構)  (知道資料庫架構時，存取資料來源。 `CDynamicAccessor` 方法會取得資料行資訊，例如資料行名稱、計數和資料類型。 您可以使用此資料行資訊，在執行時間動態建立存取子。 資料行資訊會儲存在由這個類別所建立和管理的緩衝區中。 使用 [GetValue](./cdynamicaccessor-class.md#getvalue) 方法從緩衝區取得資料。

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

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) 的運作方式類似 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，但有一個重要的方式。 `CDynamicAccessor`在以提供者所報告的原生格式要求資料時， `CDynamicStringAccessor` 要求提供者會提取從資料存放區存取的所有資料，做為字串資料。 此程式特別適用于不需要計算資料存放區中值的簡單工作，例如顯示或列印資料存放區的內容。

使用 `CDynamicStringAccessor` 方法來取得資料行資訊。 您可以使用此資料行資訊，在執行時間動態建立存取子。 資料行資訊會儲存在由這個類別所建立和管理的緩衝區中。 使用 [CDynamicStringAccessor：： GetString](./cdynamicstringaccessor-class.md#getstring) 從緩衝區取得資料，或使用 [CDynamicStringAccessor：： SetString](./cdynamicstringaccessor-class.md#setstring)將其儲存到緩衝區。

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

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 與 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)類似，不同之處在于 `CDynamicParameterAccessor` 會藉由呼叫 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 介面來取得要設定的參數資訊。 提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。

參數資訊會儲存在這個類別建立和管理的緩衝區中。 使用 [CDynamicParameterAccessor：： GetParam](./cdynamicparameteraccessor-class.md#getparam) 和 [CDynamicParameterAccessor：： GetParamType](./cdynamicparameteraccessor-class.md#getparamtype)取得緩衝區中的參數資料。

如需示範如何使用這個類別來執行 SQL Server 預存程式和取得輸出參數值的範例，請參閱 GitHub 上[Microsoft >vcsamples](https://github.com/Microsoft/VCSamples)儲存機制中的[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)範例程式碼。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
