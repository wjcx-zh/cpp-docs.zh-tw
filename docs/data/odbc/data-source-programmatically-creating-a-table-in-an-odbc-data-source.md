---
title: 以程式設計方式建立 ODBC 資料來源中的 資料表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ea8ddc8e683c0e5f0681bdf98cbddca180e4023
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>資料來源：以程式設計方式建立 ODBC 資料來源資料表
本主題說明如何建立資料表的資料來源，使用`ExecuteSQL`類別成員函式`CDatabase`，傳遞字串，其中包含此函式**CREATE TABLE** SQL 陳述式。  
  
 一般 MFC ODBC 資料來源的詳細資訊，請參閱[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。 本主題[資料來源： 以程式設計方式設定 ODBC 資料來源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)說明建立資料來源。  
  
 當您建立資料來源時，您可以輕鬆地建立資料表使用`ExecuteSQL`成員函式和**CREATE TABLE** SQL 陳述式。 例如，如果您有`CDatabase`呼叫物件`myDB`，您可以使用下列的 MFC 程式碼來建立資料表：  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 這個程式碼範例會建立名為 「 公司 」 所維護之 Microsoft Access 資料來源連接中的資料表`myDB`; 資料表包含兩個欄位 」 OfficeID"和"OfficeName。 」  
  
> [!NOTE]
>  中指定的欄位型別**CREATE TABLE** SQL 陳述式可能會根據您使用的 ODBC 驅動程式而有所不同。 Microsoft Query 程式 （隨附於 Visual c + + 1.5） 是一種方式探索資料來源的可用的欄位類型。 在查詢中，按一下 **檔案**，按一下  **Table_Definition**資料來源選取資料表，看看顯示的類型**類型**下拉式方塊。 SQL 語法也可用來建立索引。  
  
## <a name="see-also"></a>另請參閱  
 [資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)