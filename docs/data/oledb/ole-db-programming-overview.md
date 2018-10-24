---
title: OLE DB 程式設計概觀 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5fea82dfd7d3f9cdd64d0eab66e44ac1a486abac
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49989888"
---
# <a name="ole-db-programming-overview"></a>OLE DB 程式設計概觀

OLE DB 是以 COM 為基礎的高效能資料庫技術。 它提供存取資料儲存所在表單的獨立的常見方式。 在典型的企業的情況下，大量的資訊不會儲存在公司的資料庫中。 編製索引-循序檔案、 個人 （例如存取） 的資料庫、 試算表 （例如 Excel)、 專案規劃應用程式 （例如專案） 和 （例如 Outlook) 的電子郵件 （例如 FAT 或 NTFS） 的檔案系統中找到這項資訊。 OLE DB 可讓您以相同的方式，存取任何種類的資料存放區，只要資料存放區有 OLE DB 提供者。
  
OLE DB 可讓您開發應用程式以存取不同資料來源，不論它們是 DBMS 與否。 OLE DB 通用存取可讓使用適當的 DBMS 功能對給定的資料來源的 COM 介面。 COM 可減少不必要的重複資料刪除的服務，並最大化不只在資料來源之間，也在其他應用程式之間的互通性。  
  
## <a name="benefits-of-com"></a>COM 的優點  

這是 COM 之處。 OLE DB 是一組 COM 介面。 藉由透過一組一致的介面存取資料，您可以將資料庫組織成合作元件的矩陣。  
  
以 COM 規格為基礎，OLE DB 定義的可延伸且可維護的集合的因素，並將封裝的 DBMS 功能的一致、 可重複使用部分的介面。 這些介面定義資料列的容器，查詢處理器和交易協調器，可統一各種資訊來源的交易式存取等的 DBMS 元件的界限。  
 
## <a name="see-also"></a>另請參閱  

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 範本](../../data/oledb/ole-db-templates.md)