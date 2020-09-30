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
ms.openlocfilehash: f65bd0f90832039d453d84ab9765781c30750318
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507365"
---
# <a name="commands-and-tables"></a>命令和資料表

命令和資料表可讓您存取資料列集;也就是說，開啟資料列集、執行命令，以及系結資料行。 [CCommand](../../data/oledb/ccommand-class.md)和[CTable](../../data/oledb/ctable-class.md)類別會分別具現化命令和資料表物件。 這些類別衍生自 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) ，如下圖所示。

![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "CCommand 和 CTable")<br/>
命令和資料表類別

在上表中， `TAccessor` 可以是 [存取](../../data/oledb/accessors-and-rowsets.md)子類型中所列的任何存取子類型。 `TRowset` 可以是列于資料列 [集類型](../../data/oledb/accessors-and-rowsets.md)中的任何資料列集型別。 `TMultiple` 指定 (單一或多個結果集) 的結果型別。

[ATL OLE DB 取用者嚮導](../../atl/reference/atl-ole-db-consumer-wizard.md)可讓您指定是否要使用命令或資料表物件。

- 針對沒有命令的資料來源，您可以使用 `CTable` 類別。 您通常會將它用於不指定參數且不需要多個結果的簡單資料列集。 這個簡單的類別會使用您指定的資料表名稱，開啟資料來源上的資料表。

- 針對支援命令的資料來源，您可以 `CCommand` 改用類別。 若要執行命令，請在這個類別上呼叫 [Open](./ccommand-class.md#open) 。 或者，您可以呼叫 `Prepare` 來準備要執行一次以上的命令。

   `CCommand` 有三個樣板引數：存取子型別、資料列集型別，以及結果型別 (`CNoMultipleResults` 預設為或 `CMultipleResults`) 。 如果您指定 `CMultipleResults` ， `CCommand` 類別會支援 `IMultipleResults` 介面並處理多個資料列集。 [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)範例顯示如何處理多個結果。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)
