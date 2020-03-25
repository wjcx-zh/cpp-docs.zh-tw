---
title: 命令和資料表
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211519"
---
# <a name="commands-and-tables"></a>命令和資料表

命令和資料表可讓您存取資料列集;也就是開啟資料列集、執行命令和系結資料行。 [CCommand](../../data/oledb/ccommand-class.md)和[CTable](../../data/oledb/ctable-class.md)類別會分別具現化命令和 table 物件。 這些類別衍生自[CAccessorRowset](../../data/oledb/caccessorrowset-class.md) ，如下圖所示。

![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "CCommand 和 CTable")<br/>
命令和資料表類別

在上表中，`TAccessor` 可以是在[存取子類型](../../data/oledb/accessors-and-rowsets.md)中列出的任何存取子類型。 `TRowset` 可以是資料列[集類型](../../data/oledb/accessors-and-rowsets.md)中列出的任何資料列集類型。 `TMultiple` 指定結果類型（單一或多個結果集）。

「 [ATL OLE DB 取用者」 Wizard](../../atl/reference/atl-ole-db-consumer-wizard.md)可讓您指定是否要使用命令或資料表物件。

- 針對沒有命令的資料來源，您可以使用 `CTable` 類別。 您通常會將它用於不指定參數，且不需要多個結果的簡單資料列集。 這個簡單的類別會使用您指定的資料表名稱，開啟資料來源上的資料表。

- 對於支援命令的資料來源，您可以改用 `CCommand` 類別。 若要執行命令，請在這個類別上呼叫[Open](../../data/oledb/ccommand-open.md) 。 或者，您可以呼叫 `Prepare` 來準備要執行一次以上的命令。

   `CCommand` 有三個樣板引數：存取子型別、資料列集型別和結果型別（`CNoMultipleResults`預設為，或 `CMultipleResults`）。 如果您指定 `CMultipleResults`，`CCommand` 類別支援 `IMultipleResults` 介面，並處理多個資料列集。 [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)範例會示範如何處理多個結果。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)
