---
title: TN055:MFC ODBC 資料庫類別應用程式移轉至 MFC DAO 類別
ms.date: 06/20/2018
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
ms.openlocfilehash: 7a1d3436a9b19c40df2a08576d797de49833f14f
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611229"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055:MFC ODBC 資料庫類別應用程式移轉至 MFC DAO 類別

> [!NOTE]
> 視覺效果C++環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您改用[OLE DB 樣板](../data/oledb/ole-db-templates.md)或是[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO，在維護現有的應用程式。

## <a name="overview"></a>總覽

在大部分情況下，可能需要將使用 MFC 的 ODBC 資料庫類別的應用程式移轉至 MFC 的 DAO 資料庫類別。 這個技術提示將詳細說明 MFC ODBC 與 DAO 類別之間的大多數差異。 在考慮差異的情況下，如有需要，將應用程式從 ODBC 類別移轉至 MFC 類別應該不困難。

## <a name="why-migrate-from-odbc-to-dao"></a>為什麼要移轉至 DAO 的 從 ODBC

您想要將應用程式從 ODBC 資料庫類別移轉至 DAO 資料庫類別的原因有許多種，但是這項決定不見得簡單或淺顯易懂。 務必記住的是，DAO 所使用的 Microsoft Jet 資料庫引擎可以讀取您擁有其 ODBC 驅動程式的任何 ODBC 資料來源。 雖然使用 ODBC 資料庫類別或直接自行呼叫 ODBC 可能更有效率，不過 Microsoft Jet 資料庫引擎可以讀取 ODBC 資料。

以下是幾個容易決定 ODBC/DAO 的簡單情況。 例如，如果您只需要存取採用 Microsoft Jet 引擎可直接讀取之格式的資料 (Access 格式、Excel 格式等)，很明顯就是選擇使用 DAO 資料庫類別。

如果您的資料位於伺服器或各種不同的伺服器上，情況就會較為複雜。 在這種情況下，就不容易決定應使用 ODBC 資料庫類別或 DAO 資料庫類別。 如果您要進行像是異質聯結 (聯結不同伺服器上多種格式的資料，如 SQL Server 和 Oracle) 這類作業，則 Microsoft Jet 資料庫引擎將自動執行聯結，而不會強迫您執行必要的工作，就像使用 ODBC 資料庫類別或直接呼叫 ODBC 時一樣。 如果您使用的 ODBC 驅動程式支援驅動程式資料指標，最佳選擇可能是 ODBC 資料庫類別。

要做出選擇可能很複雜，因此您可能想要撰寫範例程式碼，依據您的特殊需求測試各種方法的效能。 這個技術提示假設您已決定從 ODBC 資料庫類別移轉至 DAO 資料庫類別。

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>ODBC 資料庫類別與 MFC DAO 資料庫類別之間的相似處

MFC ODBC 類別的原始設計是根據 Microsoft Access 和 Microsoft Visual Basic 中持續使用的 DAO 物件模型。 這表示，ODBC 和 MFC DAO 類別之間有許多通用的功能，不過本節中不會全部列出。 一般而言，程式設計模型都是一樣的。

以下強調幾個相似之處：

- ODBC 和 DAO 類別都有使用基礎資料庫管理系統 (DBMS) 進行管理的資料庫物件。

- 兩者都有資料錄集物件，代表一組從該 DBMS 傳回的結果。

- DAO 資料庫和資料錄集物件的成員幾乎與 ODBC 類別完全相同。

- 在這兩組類別中，除了在物件和成員名稱上有些變更之外，擷取資料的程式碼是一樣的。 雖然需要變更，不過從 ODBC 類別轉換成 DAO 類別時，名稱變更的過程相當直接。

例如，在這兩種模型中，擷取資料的程序是建立並開啟資料庫物件、建立並開啟資料錄集物件，以及巡覽 (移動) 執行某項作業的資料。

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>ODBC 和 DAO MFC 類別之間的差異

DAO 類別包含較多物件和一組內容更豐富的方法，不過，本節僅就類似類別和功能之間的差異詳細說明。

類別之間可能最顯著的差異是類似類別和全域函式的名稱變更。 下列清單將顯示與資料庫類別相關的物件、方法和全域函式的名稱變更：

|類別或函式|MFC DAO 類別中的對等用法|
|-----------------------|-----------------------------------|
|`CDatabase`|`CDaoDatabase`|
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|
|`CRecordset`|`CDaoRecordset`|
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|
|`CFieldExchange`|`CDaoFieldExchange`|
|`RFX_Bool`|`DFX_Bool`|
|`RFX_Byte`|`DFX_Byte`|
|`RFX_Int`|`DFX_Short`|
|`RFX_Long`|`DFX_Long`|
||`DFX_Currency`|
|`RFX_Single`|`DFX_Single`|
|`RFX_Double`|`DFX_Double`|
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`-基礎)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> `RFX_Date`函數會根據`CTime`和`TIMESTAMP_STRUCT`。

以下列出功能上的主要變更，這些變更可能會影響您的應用程式，並且需要進行較複雜的名稱變更。

- 常數和巨集，用來指出像是資料錄集開放類型和資料錄集開放選項已變更這類情況。

   若使用 ODBC 類別，MFC 需要透過巨集或列舉的類型定義這些選項。

   若使用 DAO 類別，DAO 會在標頭檔 (DBDAOINT.H) 中提供這些選項的定義。 因此，資料錄集類型是 `CRecordset` 的列舉成員，不過在 DAO 中則是常數。 比方說，您可使用**快照集**時指定的型別`CRecordset`ODBC 中，但**DB_OPEN_SNAPSHOT**時指定的型別`CDaoRecordset`。

- 預設資料錄集類型`CRecordset`已**快照集**時的預設資料錄集類型`CDaoRecordset`會**動態集**（請參閱下方的附註有關 ODBC 類別快照的其他問題）。

- ODBC `CRecordset` 類別可以選擇建立順向資料錄集類型。 在 `CDaoRecordset` 類別中，順向並不是資料錄集類型，而是特定資料錄集類型的屬性 (或選項)。

- 開啟 `CRecordset` 物件時的僅附加資料錄集，是指可以讀取和附加資料錄集的資料。 若使用 `CDaoRecordset` 物件，僅附加選項實際上是表示資料錄集的資料只能附加 (而不能讀取)。

- ODBC 類別的異動成員函式是 `CDatabase` 的成員，並且會在資料庫層級執行動作。 在 DAO 類別中，異動成員函式是較高層級類別 (`CDaoWorkspace`) 的成員，因此可能會影響共用同一個工作區 (異動空間) 的多個 `CDaoDatabase` 物件。

- 例外狀況類別已變更。 `CDBExceptions` ODBC 類別中擲回和`CDaoExceptions`在 DAO 類別中。

- `RFX_Date` 會使用`CTime`並`TIMESTAMP_STRUCT`物件，而`DFX_Date`使用`COleDateTime`。 `COleDateTime`幾乎等同`CTime`，但是為依據的 8 位元 OLE**日期**而不是 4 位元組**time_t**因此能夠保存更大範圍的資料。

   > [!NOTE]
   > DAO (`CDaoRecordset`) 快照是唯讀的，而 ODBC (`CRecordset`) 快照可能可以根據 ODBC 資料指標程式庫的驅動程式和用途更新。 如果您使用的是資料指標程式庫，`CRecordset` 快照就可以更新。 如果您使用的是 Desktop Driver Pack 3.0 中任何不含 ODBC 資料指標程式庫的 Microsoft 驅動程式，則 `CRecordset` 快照是唯讀的。 如果您使用其他驅動程式，請檢查驅動程式的文件，以查看快照集 (`STATIC_CURSORS`) 都是唯讀。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
