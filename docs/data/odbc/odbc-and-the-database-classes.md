---
title: ODBC 和資料庫類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: abbb20b76f8e24a9b0f20961728dd8e428733654
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088463"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和資料庫類別
MFC ODBC 資料庫類別封裝在您將正常自行在成員函式的 ODBC API 函式呼叫[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)類別。 例如，複雜的 ODBC 呼叫順序，傳回記錄的儲存位置、 處理錯誤狀況和其他作業的繫結會為您管理資料庫類別。 如此一來，您可以使用相當簡單的類別介面來透過資料錄集物件。  
  
> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。  
  
 雖然資料庫類別會封裝 ODBC 的功能，但不提供一對一對應的 ODBC API 函式。 資料庫類別提供更高的抽象概念，建立模型之後 Microsoft Access 和 Microsoft Visual Basic 中找到資料存取物件。 如需詳細資訊，請參閱[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)