---
title: 存取 ODBC 和 SQL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4fb5daa988614e7e9cb058fce183c6af5b50dd30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087812"
---
# <a name="access-to-odbc-and-sql"></a>存取 ODBC 和 SQL
Mfc 程式庫封裝的多個 Windows 應用程式開發介面呼叫，並仍然可讓您直接呼叫任何 Windows API 函式。 資料庫類別可讓您充分 ODBC API 相同的彈性。 資料庫類別可避免您的 ODBC 的複雜性，而您可以直接從任何地方呼叫 ODBC API 函式在程式中。  
  
 同樣地，資料庫類別免除您不必使用方式，就與[SQL](../../data/odbc/sql.md)，但是您可以使用 SQL 直接如果您想要。 您可以自訂資料錄集物件，藉由傳遞自訂的 SQL 陳述式 （或預設的陳述式設定部份） 當您開啟資料錄集。 您也可以進行使用直接 SQL 呼叫[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)類別成員函式[CDatabase](../../mfc/reference/cdatabase-class.md)。  
  
 如需詳細資訊，請參閱[ODBC： 直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)和[SQL： 製作直接 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)