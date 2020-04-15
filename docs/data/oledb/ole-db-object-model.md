---
title: OLE DB 物件模型
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369802"
---
# <a name="ole-db-object-model"></a>OLE DB 物件模型

OLE DB 物件模型由以下物件或元件組成。 列出的前四個物件或元件(資料源、作業階段、命令和行集)允許您連接到資料源並查看它。 其餘的,從訪問器開始,與在顯示數據時處理數據有關。

## <a name="data-sources"></a>資料來源

數據源物件允許您連接到數據來源(如檔案或 DBMS)。 數據源物件創建和管理連接,並包含許可權和身份驗證資訊(如登錄名和密碼)。 數據源物件可以創建一個或多個工作階段。

## <a name="sessions"></a>工作階段

會話管理與數據源的特定交互以查詢和檢索數據。 每個會話都是單個事務。 事務是由 ACID 測試定義的不可分割的工作單元。 有關 ACID 的定義,請參閱[事務](#vcconoledbcomponents_transactions)。

會話執行重要任務,如打開行集並返回創建它的數據源物件。 會話還可以返回元數據或有關數據源本身的資訊(如表資訊)。

會話可以創建一個或多個命令。

## <a name="commands"></a>命令

命令執行文字命令(如 SQL 語句)。 如果文字命令指定行集(如 SQL **SELECT**語句),則該命令將創建行集。

命令只是文本命令的容器,它是從消費者傳遞到數據源物件的字串(如 SQL 語句),供提供程式的基礎數據儲存執行。 通常,文本命令是 SQL **SELECT**語句(在這種情況下,由於 SQL **SELECT**指定了行集,命令會自動創建一個行集)。

## <a name="rowsets"></a>資料列集

行集以表格格式顯示資料。 索引是行集的特殊情況。 可以從會話或命令創建行集。

### <a name="schema-rowsets"></a>結構描述資料列集

架構具有有關資料庫的元數據(結構資訊)。 架構行集是具有架構資訊的行集。 DBMS 的某些 OLE DB 提供程式支援架構排組物件。 有關架構列集的詳細資訊,請參閱[使用架構列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[架構行集類和 Typedef 類](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)獲取元數據。

### <a name="view-objects"></a>檢視物件

視圖物件定義行集中的行和列的子集。 它沒有自己的數據。 視圖物件無法合併來自多個行集的數據。

## <a name="accessors"></a>存取子

只有 OLE DB 使用訪問器的概念。 訪問器描述數據在消費者中的儲存方式。 它在行集欄位(列)和在消費者中聲明的數據成員之間具有一組綁定(稱為列映射)。

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>交易

在以最低級別以外的其他級別提交或中止嵌套事務時,將使用事務物件。 事務是由 ACID 測試定義的不可分割的工作單元。 ACID 代表:

- 原子性,不能分為較小的工作單元

- 併發,一次可以發生多個事務

- 隔離,一個事務對另一個事務所做的更改瞭解有限

- 持久性,事務進行持續更改

## <a name="enumerators"></a>列舉值

枚舉器搜索可用的數據源和其他枚舉器。 未為特定數據源自定義的消費者使用枚舉器搜索要使用的數據源。

在 Microsoft 資料訪問 SDK 中附帶的根枚舉器將遍歷註冊表,查找數據源和其他枚舉器。 其他枚舉者遍歷註冊表或以特定於提供程式的方式進行搜索。

## <a name="errors"></a>Errors

任何 OLE DB 物件上的任何介面都可能產生錯誤。 錯誤包含有關錯誤的其他資訊,包括可選的自定義錯誤物件。 此資訊存儲在 HRESULT 中。

## <a name="notifications"></a>通知

共用行集的合作消費者組使用通知(其中共享意味著假定消費者在同一事務中工作)。 通知使共用行集的協作使用者能夠瞭解其對等方執行的行集上的操作。

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 編程概述](../../data/oledb/ole-db-programming-overview.md)
