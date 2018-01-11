---
title: "使用動態存取子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3d2e722ce96ff7a2f1add779377079a0eaecfc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-dynamic-accessors"></a>使用動態存取子
動態存取子會讓您存取資料來源，當您在不知道資料庫結構描述 （基礎結構）。 OLE DB 樣板程式庫提供數種類別可以幫助您執行這項操作。  
  
 [DynamicConsumer](http://msdn.microsoft.com/en-us/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)範例示範如何使用動態存取子類別，以擷取資料行資訊，以動態方式建立存取子。  
  
## <a name="using-cdynamicaccessor"></a>使用 CDynamicAccessor  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)可讓您存取資料來源，當您在不知道資料庫結構描述 （資料庫的基礎結構）。 `CDynamicAccessor`方法會取得資料行資訊，例如資料行名稱、 計數和資料類型。 您可以使用此資料行資訊在執行階段動態建立存取子。 資料行資訊會儲存在緩衝區中，建立和管理由這個類別。 取得資料緩衝區使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)方法。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// Using_Dynamic_Accessors.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
  
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
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            DBTYPE type;  
            rs.GetColumnType( i, &type );  
            printf_s( "Column %d [%S] is of type %d\n",  
                      i, rs.GetColumnName( i ), type );   
  
            switch( type )  
            {  
                case DBTYPE_WSTR:  
                    printf_s( "value is %S\n",  
                              (WCHAR*)rs.GetValue( i ) );  
                break;  
                case DBTYPE_STR:  
                    printf_s( "value is %s\n",  
                              (CHAR*)rs.GetValue( i ) );  
                default:  
                    printf_s( "value is %d\n",  
                              *(long*)rs.GetValue( i ) );  
            }  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
    return 0;  
}  
```  
  
## <a name="using-cdynamicstringaccessor"></a>使用 CDynamicStringAccessor  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)運作方式類似[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，除非有一個重要的差異。 雖然`CDynamicAccessor`要求提供者，所報告的原生格式資料`CDynamicStringAccessor`要求提供者擷取從資料存放區做為字串資料存取的所有資料。 這是不需要計算值的資料存放區，例如顯示或列印的資料存放區內容的簡單工作特別有用。  
  
 使用`CDynamicStringAccessor`方法，取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。 資料行資訊會儲存在緩衝區中建立和管理由這個類別。 取得資料緩衝區使用[cdynamicstringaccessor:: Getstring](../../data/oledb/cdynamicstringaccessor-getstring.md)或將它存放至緩衝區使用[cdynamicstringaccessor:: Setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// Using_Dynamic_Accessors_b.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
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
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            printf_s( "column %d value is %s\n",   
                      i, rs.GetString( i ) );  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
   return 0;  
  
}  
```  
  
## <a name="using-cdynamicparameteraccessor"></a>使用 CDynamicParameterAccessor  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)類似於[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，不同之處在於`CDynamicParameterAccessor`取得參數資訊，將藉由呼叫[ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx)介面。 提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。  
  
 參數資訊會儲存在這個類別建立和管理的緩衝區中。 從緩衝區取得參數資料使用[cdynamicparameteraccessor:: Getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md)和[cdynamicparameteraccessor:: Getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)。  
  
 如需如何使用這個類別執行 SQL Server 預存程序並取得輸出參數值的範例示範，請參閱知識庫文章 Q058860＜如何：使用 CDynamicParameterAccessor 執行預存程序＞。 知識庫文件可在 MSDN Library 中的 Visual Studio 文件或在[http://support.microsoft.com](http://support.microsoft.com/)。  
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [DynamicConsumer 範例](http://msdn.microsoft.com/en-us/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)