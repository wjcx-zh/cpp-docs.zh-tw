---
title: OLE DB 架構設計問題 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7dbc9b361dd04956803dde42f73f0d757b10b8b3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726384"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 架構設計問題
啟動 OLE DB 應用程式之前，您應該考慮下列問題：  
  
## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>您將撰寫您的 OLE DB 應用程式使用何種程式設計實作？

Microsoft 提供數個程式庫，以完成這項作業： OLE DB 樣板程式庫、 OLE DB 屬性和 OLE DB SDK 中的原始 OLE DB 介面。 此外，還有精靈可幫助您撰寫您的程式。 這些實作所述[OLE DB 樣板、 屬性和其他實作](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)。

## <a name="do-you-need-to-write-your-own-provider"></a>您需要撰寫您自己的提供者嗎？

大部分的開發人員不需要撰寫自己的提供者。 Microsoft 提供數個提供者。 您在建立資料連線 （例如，當您新增至您的專案使用 ATL OLE DB 消費者精靈的取用者），每當**資料連結屬性**對話方塊會列出在您的系統上註冊的所有可用提供者。 如果其中一個提供者是適用於您自己的資料存放區和資料存取應用程式，最簡單的做法是使用其中一種。 不過，如果您的資料存放區不符合其中一個類別，您必須建立自己的提供者。 如需建立提供者的資訊，請參閱[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)。

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>您需要為您的取用者的支援層級？

部分取用者可以是非常基本;雖然其他人可能會很複雜。 屬性會指定 OLE DB 物件的功能。 當您使用 [ATL OLE DB 消費者精靈] 來建立取用者或資料庫提供者精靈來建立提供者時，它會設定適當的物件屬性，以提供您一組標準的功能。 不過，如果精靈產生的取用者或提供者類別不支援您需要它們來執行的所有項目，您需要的介面中的這些類別是指[OLE DB 樣板程式庫](../../data/oledb/ole-db-templates.md)。 這些介面來包裝原始的 OLE DB 介面，提供額外的實作，讓您使用起來更容易為您。

比方說，如果您想要更新的資料列集中的資料，但忘記指定這，當您使用精靈建立消費者時，您可以指定的功能在事實之後藉由設定`DBPROP_IRowsetChange`和`DBPROP_UPDATABILITY`命令物件上的屬性。 然後，建立資料列集時，它會使`IRowsetChange`介面。

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>您有舊版的程式碼使用另一個資料存取技術 （ADO、 ODBC 或 DAO） 嗎？

指定技術 （例如 ADO 元件使用 OLE DB 元件，並將 ODBC 程式碼移轉到 OLE DB） 的可能組合，涵蓋所有情況下是超出範圍的 Visual c + + 文件。 然而，許多文章，內容涵蓋各種案例的下列 Microsoft 網站：

- [Microsoft 說明和支援](https://support.microsoft.com/)

- [Microsoft 資料存取技術文件概觀](https://msdn.microsoft.com/en-us/library/ms810811.aspx)

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)
