---
title: OLE DB 架構設計問題
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: ef2837ea80c61f074cf567ee1fe61fa2cfa0ae73
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525310"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 架構設計問題

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

啟動 OLE DB 應用程式之前，請考慮下列問題：

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>您將使用何種程式設計實作來撰寫您的 OLE DB 應用程式？

Microsoft 提供數個程式庫來完成此工作：OLE DB 範本庫、OLE DB 屬性和 OLE DB SDK 中的原始 OLE DB 介面。 此外，還有一些精靈可幫助您撰寫程式。 這些實作詳述於 [OLE DB 範本、屬性和其他實作](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)中。

## <a name="do-you-need-to-write-your-own-provider"></a>您需要撰寫自己的提供者嗎？

大部分的開發人員不需要撰寫自己的提供者。 Microsoft 提供數個提供者。 每當您建立資料連線 (例如，當您使用 **ATL OLE DB 消費者精靈**將取用者新增至您的專案) 時，[資料連結屬性] 對話方塊會列出在您系統上註冊的所有可用提供者。 如果其中一個提供者適用於您自己的資料存放區和資料存取應用程式，最簡單的做法是使用其中一種。 不過，如果您的資料存放區不符合其中一個類別，您必須建立自己的提供者。 如需有關建立提供者的資訊，請參閱 [OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)。

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>您的取用者需要哪種層級的支援？

部分取用者可以是基本的，但是部分取用者可以是複雜的。 OLE DB 物件的功能會透過屬性指定。 當您使用 **ATL OLE DB 消費者精靈**來建立取用者，或使用**資料庫提供者精靈**來建立提供者時，它會為您設定適當的物件屬性，以提供一組標準的功能。 不過，如果精靈產生的取用者或提供者類別不支援您需要它們執行的所有項目，則您需要在 [OLE DB 範本庫](../../data/oledb/ole-db-templates.md)中參考這些類別的介面。 這些介面會包裝原始的 OLE DB 介面，進而提供額外的實作，讓您使用起來更容易。

例如，如果您想要更新資料列集中的資料，但在使用精靈建立取用者時忘記指定這個功能，您可以在命令物件上設定 `DBPROP_IRowsetChange` 和 `DBPROP_UPDATABILITY` 屬性之後指定該功能。 接著在建立資料列集時，它就會擁有 `IRowsetChange` 介面。

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>您有使用其他資料存取技術 (ADO、ODBC 或 DAO) 的舊版程式碼嗎？

考慮到技術的可能組合 (例如使用 ADO 元件搭配 OLE DB 元件，以及將 ODBC 程式碼移轉到 OLE DB)，涵蓋所有情況已經超出 Visual C++ 文件的範圍。 不過，涵蓋多種情況的許多文章都可以在下列 Microsoft 網站上取得：

- [Microsoft 說明和支援](https://support.microsoft.com/)

- [Microsoft 資料存取技術文章概觀](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)
