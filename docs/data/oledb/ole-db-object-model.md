---
title: OLE DB 物件模型
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210115"
---
# <a name="ole-db-object-model"></a>OLE DB 物件模型

OLE DB 物件模型是由下列物件或元件所組成。 列出的前四個物件或元件（資料來源、會話、命令和資料列集）可讓您連接到資料來源並加以查看。 其餘部分（從存取子開始）與在顯示資料時使用的相關。

## <a name="data-sources"></a>資料來源

資料來源物件可讓您連接到資料來源，例如檔案或 DBMS。 資料來源物件會建立並管理連接，並包含許可權和驗證資訊（例如登入名稱和密碼）。 資料來源物件可以建立一或多個會話。

## <a name="sessions"></a>工作階段

會話會管理與資料來源的特定互動，以查詢和抓取資料。 每個會話都是單一交易。 交易是由 ACID 測試定義的不可分割工作單位。 如需 ACID 的定義，請參閱[交易](#vcconoledbcomponents_transactions)。

會話會執行重要工作，例如開啟資料列集，並傳回建立它的資料來源物件。 會話也可以傳回中繼資料，或是資料來源本身的相關資訊（例如資料表資訊）。

會話可以建立一或多個命令。

## <a name="commands"></a>命令

命令會執行 SQL 語句之類的文字命令。 如果 text 命令指定資料列集，例如 SQL **SELECT**語句，此命令就會建立資料列集。

命令只是文字命令的容器，它是從取用者傳遞至資料來源物件以供提供者的基礎資料存放區執行的字串（例如 SQL 語句）。 一般來說，text 命令是 SQL **select**語句（在此情況下，因為 sql **select**會指定資料列集，所以命令會自動建立資料列集）。

## <a name="rowsets"></a>資料列集

資料列集會以表格格式顯示資料。 索引是資料列集的特殊案例。 您可以從會話或命令建立資料列集。

### <a name="schema-rowsets"></a>結構描述資料列集

架構具有資料庫的中繼資料（結構化資訊）。 架構資料列集是具有架構資訊的資料列集。 DBMS 的部分 OLE DB 提供者支援架構資料列集物件。 如需架構資料列集的詳細資訊，請參閱[取得架構資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和架構資料列集[類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)的中繼資料。

### <a name="view-objects"></a>View 物件

View 物件會從資料列集定義資料列和資料行的子集。 它本身沒有任何資料。 View 物件無法合併多個資料列集的資料。

## <a name="accessors"></a>取值

只有 OLE DB 會使用存取子的概念。 存取子描述資料如何儲存在取用者中。 它具有一組系結（稱為「資料行對應」），這是您在取用者中宣告的資料列集欄位（資料行）和資料成員之間的系結。

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> 交易

交易對象是在認可或中止位於最低層級以外的嵌套交易時使用。 交易是由 ACID 測試定義的不可分割工作單位。 ACID 代表：

- 不可部分完成性，無法分成較小的工作單位

- 並行，一次可能會發生多個交易

- 隔離，一筆交易對其他人所做的變更有有限的瞭解

- 持久性，交易會進行持續性變更

## <a name="enumerators"></a>列舉值

枚舉器會搜尋可用的資料來源和其他枚舉器。 未針對特定資料來源自訂的取用者，會使用枚舉器來搜尋要使用的資料來源。

在 Microsoft Data Access SDK 中隨附的根枚舉器會進行登錄，以尋找資料來源和其他列舉值。 其他枚舉器會以提供者特定的方式來流覽登錄或搜尋。

## <a name="errors"></a>Errors

任何 OLE DB 物件上的任何介面都可能產生錯誤。 錯誤會有錯誤的其他相關資訊，包括選擇性的自訂錯誤物件。 這項資訊會儲存在 HRESULT 中。

## <a name="notifications"></a>通知

共用資料列集的共同取用者群組會使用通知（其中共用表示會假設取用者在相同的交易中運作）。 通知可讓共用的取用者共用資料列集，以在其對等所執行的資料列集上收到動作的通知。

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)
