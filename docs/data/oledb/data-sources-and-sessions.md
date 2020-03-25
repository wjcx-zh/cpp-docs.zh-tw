---
title: 資料來源和工作階段
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211051"
---
# <a name="data-sources-and-sessions"></a>資料來源和工作階段

下圖顯示支援連接和存取資料來源的類別。 每個類別都是以標準 OLE DB 元件實作為基礎。

![資料來源和會話類別](../../data/oledb/media/vcdatasourcesessionclasses.gif "資料來源和工作階段類別") <br/>
資料來源與工作階段類別

類別包括：

- [CDataSource](../../data/oledb/cdatasource-class.md)這個類別會具現化資料來源物件，它會透過 OLE DB 提供者，建立和管理與資料來源的連接。 資料來源會以連接字串的形式取得資料來源位址和驗證資訊等資訊。

   也值得注意的是，協助程式類別[CEnumerator](../../data/oledb/cenumerator-class.md)通常會在建立連線之前使用，以取得在系統上註冊的可用提供者清單。 這可讓您選取提供者做為資料來源。 例如，[**資料連結屬性**] 對話方塊會使用此類別來填入 [**提供者**] 索引標籤上的提供者清單。它等同于 `SQLBrowseConnect` 或 `SQLDriverConnect` 函數。

- [CSession](../../data/oledb/csession-class.md)這個類別會具現化會話物件，這代表資料來源的單一存取會話。 不過，您可以在資料來源上建立多個會話。 您可以針對每個會話建立資料列集、命令和其他物件，以從資料來源存取資料。 會話會處理交易。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)
