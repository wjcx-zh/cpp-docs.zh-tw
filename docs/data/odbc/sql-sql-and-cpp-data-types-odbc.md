---
title: "SQL: SQL 和 c + + 資料類型 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76a4f2bb14b7878c8843dc89bece4fdd5b2e3c02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 資料類型 (ODBC)
> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱"比較的 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"DAO [說明] 中的主題。  
  
 下表將 ANSI SQL 資料類型對應至 c + + 資料類型。 這可以讓指定的附錄 D 中的 C 語言資訊加強*ODBC SDK* *程式設計人員參考*MSDN Library CD 上。 精靈會管理您大部分的資料類型對應。 如果您不使用精靈，您可以使用對應資訊可協助您手動撰寫欄位交換程式碼。  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL 資料類型對應至 c + + 資料類型  
  
|ANSI SQL 資料類型|C++ 資料型別|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**整數**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**數值**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**位元**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**二進位**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**時間**|**CTime、 CString**|  
|**時間戳記**|**CTime、 CString**|  
  
 1. ANSI**十進位**和**數值**對應至`CString`因為**SQL_C_CHAR**是預設 ODBC 傳輸類型。  
  
 2. 根據預設，當對應至截斷超過 255 個字元的字元資料`CString`。 您可以藉由明確地設定擴充截斷長度`nMaxLength`引數的`RFX_Text`。  
  
 3. 二進位資料超過 255 個字元會截斷對應至預設`CByteArray`。 您可以藉由明確地設定擴充截斷長度`nMaxLength`引數的`RFX_Binary`。  
  
 如果您不會使用 ODBC 資料指標程式庫，您可能會遇到問題時嘗試更新兩個或更多長時間的可變長度欄位使用的 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類別。 ODBC 型別**SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**、 對應至文字和影像 SQL Server 類型。 A`CDBException`更新兩個或多個在相同呼叫長時間的可變長度欄位便會擲回`CRecordset::Update`。 因此，不會更新同時使用多個長資料行`CRecordset::Update`。 您可以使用 ODBC API，同時更新多個長資料行**SQLPutData**。 您也可以使用 ODBC 資料指標程式庫，但不是建議使用的驅動程式，如 SQL Server 驅動程式支援資料指標，而且不需要資料指標程式庫。  
  
 如果您使用 MFC ODBC 資料庫類別和 Microsoft SQL Server ODBC 驅動程式，使用 ODBC 資料指標程式庫**ASSERT**可能會發生連同`CDBException`如果呼叫`CRecordset::Update`呼叫之後`CRecordset::Requery`。 請改為呼叫`CRecordset::Close`和`CRecordset::Open`而不是`CRecordset::Requery`。 另一個解決方案就是不要使用 ODBC 資料指標程式庫，因為 SQL Server 和 SQL Server ODBC 驅動程式提供原生支援資料指標的原生而且不需要 ODBC 資料指標程式庫。  
  
## <a name="see-also"></a>另請參閱  
 [SQL](../../data/odbc/sql.md)   
 [SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)