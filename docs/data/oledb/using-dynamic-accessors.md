---
title: "使用動態存取子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取子 [C++], 動態"
  - "動態存取子"
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用動態存取子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

動態存取子可以讓您在不知道資料庫結構描述 \(基礎結構\) 時存取資料來源。  OLE DB 樣板程式庫提供了幾種可以幫助您達成此目的之類別。  
  
 [DynamicConsumer](http://msdn.microsoft.com/zh-tw/2ccc4c61-6749-4e83-aa81-00f8009c0dc3) 範例將顯示使用動態存取子類別取得資料行資訊和動態地建立存取子的方法。  
  
## 使用 CDynamicAccessor  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 能讓您在不知道資料庫結構描述 \(資料庫的基礎結構\) 的情況下，存取資料來源。  `CDynamicAccessor` 方法會取得資料行資訊，例如資料行名稱、計數和資料型別。  您可以在執行階段使用這些資料行資訊，動態地建立存取子。  資料行資訊儲存於這個類別所建立和管理的暫存區中。  使用 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) 方法便可以取得這份位於暫存區的資料。  
  
## 範例  
  
### 程式碼  
  
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
  
## 使用 CDynamicStringAccessor  
 除了某個重要部分，[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) 的作用很相似於 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)。  `CDynamicAccessor` 要求資料必須是提供者報告時的原型格式，而 `CDynamicStringAccessor` 則要求提供者以字串資料方式擷取從資料存放區存取的所有資料。  這個對於不需要計算資料存放區值的簡單工作 \(例如，顯示或列印資料存放區的內容\) 來說相當有用。  
  
 使用 `CDynamicStringAccessor` 方法取得資料行資訊。  您可以在執行階段使用這些資料行資訊，動態地建立存取子。  資料行資訊是儲存在這個類別所建立和管理的暫存區中。  使用 [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) 從緩衝區取得這份資料，或使用 [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md) 將它儲存在緩衝區中。  
  
## 範例  
  
### 程式碼  
  
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
  
## 使用 CDynamicParameterAccessor  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 的作用和 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 相類似，除了 `CDynamicParameterAccessor` 是呼叫 [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) 介面以取得設定的參數資訊。  提供者必須支援消費者的 `ICommandWithParameters` 才能使用這個類別。  
  
 參數資訊是儲存於這個類別所建立和管理的暫存區中。  使用 [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md) 便可以取得暫存區的參數資料。  
  
 如需示範使用這個類別以執行 SQL Server 預存程序和取得輸出參數值的方法範例，請參閱知識庫 \(Knowledge Base\) 文件 Q058860＜HOWTO: Execute Stored Procedure using CDynamicParameterAccessor＞。知識庫文件位於 MSDN Library for Visual Studio 文件中或是 [http:\/\/support.microsoft.com](http://support.microsoft.com/)。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [DynamicConsumer Sample](http://msdn.microsoft.com/zh-tw/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)