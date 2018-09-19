---
title: ODBC 和資料庫類別 |Microsoft Docs
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
ms.openlocfilehash: bce3140818b46bd6cbb255794a08e9b0fa92fbd4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114965"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和資料庫類別

您會通常在自己的成員函式的 ODBC API 函式呼叫的 MFC ODBC 資料庫類別封裝[CDatabase](../../mfc/reference/cdatabase-class.md)並[CRecordset](../../mfc/reference/crecordset-class.md)類別。 例如，複雜的 ODBC 呼叫順序，傳回的記錄到儲存體位置、 處理錯誤狀況，以及其他作業的繫結會為您管理的資料庫類別。 如此一來，您可以使用相當簡單的類別介面來透過資料錄集物件。  
  
> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。  
  
雖然資料庫類別封裝 ODBC 的功能，但不提供 ODBC API 函式的一對一對應。 資料庫類別會提供較高層級的抽象概念，建立模型之後找到 Microsoft Access 和 Microsoft Visual Basic 中的資料存取物件。 如需詳細資訊，請參閱 < [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  

[ODBC 基本概念](../../data/odbc/odbc-basics.md)