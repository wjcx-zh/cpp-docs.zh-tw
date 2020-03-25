---
title: ODBC 和資料庫類別
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213158"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和資料庫類別

MFC ODBC 資料庫類別會封裝您通常會在[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)類別的成員函式中執行的 odbc API 函式呼叫。 例如，複雜的 ODBC 呼叫順序、傳回的記錄與儲存位置的系結、錯誤狀況的處理，以及其他作業，都是由資料庫類別來管理。 因此，您可以使用更簡單的類別介面，透過記錄集物件來操作記錄。

> [!NOTE]
>  您可以透過 MFC ODBC 類別存取 ODBC 資料來源，如本主題中所述，或透過 MFC 資料存取物件（DAO）類別。

雖然資料庫類別會封裝 ODBC 功能，但它們並不提供 ODBC API 函式的一對一對應。 資料庫類別提供較高層級的抽象概念，並在 Microsoft Access 和 Microsoft Visual Basic 中找到的資料存取物件之後建立模型。 如需詳細資訊，請參閱[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)
