---
title: 資料錄集：動態地繫結資料行 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: 8bc9ba8a143234bec7927c9578a69a95a511bb9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837784"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>資料錄集：動態地繫結資料行 (ODBC)

本主題適用於 MFC ODBC 類別。

資料錄集會管理繫結您在設計階段指定的資料表資料行，但有時您可能想要繫結您在設計階段還不知道的資料行。 本主題將說明：

- [當您可能想要將資料行動態繫結至資料錄集時](#_core_when_you_might_bind_columns_dynamically)。

- [如何在執行階段動態繫結資料行](#_core_how_to_bind_columns_dynamically)。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您要使用大量資料列擷取，則不建議使用一般說明的技術。 如需大量資料列提取的詳細資訊，請參閱 [記錄集：大量提取記錄 (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a> 當您可能要動態繫結資料行時

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

在設計階段，MFC 應用程式精靈或 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (來自 [加入類別]****) 會根據資料來源的已知資料表和資料行來建立資料錄集類別。 資料庫可以在您設計它們時，以及稍後當您的應用程式在執行階段使用那些資料表和資料行時之間進行變更。 您或其他使用者可能會加入或卸除資料表，或者從應用程式的資料錄集所依賴的資料表中加入或卸除資料行。 您可能不需為所有資料存取應用程式考量這點，但如果它適合您，則您該如何設法解決資料庫結構描述中的變更，而非重新設計並重新編譯？ 本主題的目的是回答這個問題。

本主題說明您可能動態繫結資料行的最常見案例：從以已知資料庫結構描述為基礎的資料錄集開始，您想要在執行階段處理其他資料行。 本主題進一步假設其他資料行會對應至 `CString` 欄位資料成員，儘管已提供建議來協助您管理其他資料型別，但此為最常見的案例。

使用少量的額外程式碼，您可以：

- [判斷哪些資料行可在執行階段使用](#_core_how_to_bind_columns_dynamically)。

- [在執行階段將其他資料行動態繫結至您的資料錄集](#_core_adding_the_columns)。

您的資料錄集仍會包含您已在設計階段知道之資料行的資料成員。 它也會包含少量的額外程式碼，可動態判斷是否已將任何新的資料行加入至您的目標資料表，而且如果是這樣，請將這些新的資料行繫結至動態配置的儲存空間 (而非繫結至資料錄集資料成員)。

本主題並未涵蓋其他動態繫結案例，例如，已卸除的資料表或資料行。 針對那些案例，您需要更直接使用 ODBC API 呼叫。 如需詳細資訊，請參閱《 ODBC 程式設計 [人員參考](/sql/odbc/reference/odbc-programmer-s-reference)》。

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a> 如何動態繫結資料行

若要動態繫結資料行，您必須知道 (或能夠判斷) 額外資料行的名稱。 您也必須為其他欄位資料成員配置儲存空間、指定其名稱及型別，然後指定要加入的資料行數目。

以下討論將提及兩個不同的資料錄集。 第一個是從目標資料表中選取資料錄的主要資料錄集。 第二個是特殊資料行資料錄集，可用來取得目標資料表中資料行的相關資訊。

### <a name="general-process"></a><a name="_core_the_general_process"></a> 一般流程

在最普通的層級上，遵循下列步驟：

1. 建構主要資料錄集物件。

   選擇性地將指標傳遞給 `CDatabase` 開啟物件，或者能夠以一些其他方式來提供資料行資料錄集的連線資訊。

1. 採取步驟，以便動態加入資料行。

   請參閱以下「加入資料行」中所述的流程。

1. 開啟主要資料錄集。

   資料錄集會選取資料錄，並使用資料錄欄位交換 (RFX) 來繫結靜態資料行 (那些會對應至資料錄集的欄位資料成員) 和動態資料行 (對應至您所配置的額外儲存空間)。

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a> 加入資料行

在執行階段動態繫結已加入的資料行需要下列步驟：

1. 判斷在執行階段中哪些資料行位於目標資料表。 從自您的資料錄集類別設計以來已加入至資料表之資料行清單中擷取該資訊。

   有個不錯的方法是使用設計來查詢資料來源的資料行資料錄集類別，來取得目標資料表的資料行資訊 (例如，資料行名稱和資料型別)。

1. 為新的欄位資料成員提供儲存空間。 由於您的主要資料錄集類別沒有適用於未知資料行的欄位資料成員，因此，您必須提供一個位置來儲存名稱、結果值，以及可能的資料型別資訊 (如果資料行均為不同的資料型別)。

   其中一個方法是建置一或多個動態清單，一個用於新資料行的名稱、另一個用於它們的結果值，而第三個用於它們的資料型別 (如有必要)。 這些清單 (特別是值清單) 會針對繫結提供資訊及所需的儲存空間。 下圖說明如何建置清單。

   ![建立要動態繫結的資料行清單](../../data/odbc/media/vc37w61.gif "建立要動態繫結的資料行清單")<br/>
   建置要動態繫結的資料行清單

1. 針對每個已加入的資料行，在主要資料錄集的 `DoFieldExchange` 函式中加入 RFX 函式呼叫。 這些 RFX 呼叫會執行下列工作：擷取資料錄 (包括其他資料行)，並將資料行繫結至資料錄集資料成員，或繫結至您以動態方式為其提供的儲存空間。

   其中一個方法是將迴圈加入至主要資料錄集的 `DoFieldExchange` 函式，以便迴圈處理新的資料行清單，其會針對清單中的每個資料行，呼叫適當的 RFX 函式。 在每個 RFX 呼叫上，傳遞來自資料行名稱清單的資料行名稱，以及結果值清單之對應成員中的儲存位置。

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a> 資料行清單

下表顯示您需要用到的四個清單。

| 清單 | 描述 |
|--|--|
| **Current-Table-Columns** | (圖中的清單 1) 目前在資料來源上之資料表中的資料行清單。 此清單可能會比對資料錄集中目前繫結的資料行清單。 |
| **Bound-Recordset-Columns** | (圖中的清單 2) 資料錄集中繫結的資料行清單。 這些資料行在 `DoFieldExchange` 函式中已經有 RFX 陳述式。 |
| **Columns-To-Bind-Dynamically** | (圖中的清單 3) 位於資料表但不在資料錄集中的資料行清單。 這些是您想要動態繫結的資料行。 |
| **Dynamic-Column-Values** | (圖中的清單 4) 此清單包含從動態繫結的資料行中擷取之值的儲存空間。 此清單的元素會以一對一方式對應至 Columns-to-Bind-Dynamically 中的元素。 |

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a> 建置您的清單

考慮到一般策略，您可以轉向詳細資料。 本主題其餘部分中的程序將示範如何建置[資料行清單](#_core_lists_of_columns)中所示的清單。 程序將引導您：

- [判斷不在資料錄集中的資料行名稱](#_core_determining_which_table_columns_are_not_in_your_recordset)。

- [為新加入至資料表的資料行提供動態儲存空間](#_core_providing_storage_for_the_new_columns)。

- [為新的資料行動態加入 RFX 呼叫](#_core_adding_rfx_calls_to_bind_the_columns)。

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> 判斷哪些資料表資料行不在資料錄集中

建置清單 (Bound-Recordset-Columns，如圖中的清單 2)，其中包含已在主要資料錄集中繫結的資料行清單。 接著，建置清單 (Columns-to-Bind-Dynamically，衍生自 Current-Table-Columns 和 Bound-Recordset-Columns)，其中包含位於資料來源的資料表，但不在主要資料錄集中的資料行名稱。

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>判斷不在資料錄集 (Columns-to-Bind-Dynamically) 中的資料行名稱

1. 建置已在主要資料錄集中繫結的資料行清單 (Bound-Recordset-Columns)。

   其中一個方法是在設計階段建立 Bound-Recordset-Columns。 您可以在資料錄集的 `DoFieldExchange` 函式中以視覺化方式檢查 RFX 函式呼叫，以取得這些名稱。 接著，將清單設定為使用名稱初始化的陣列。

   例如，此圖顯示含三個元素的 Bound-Recordset-Columns (清單 2)。 Bound-Recordset-Columns 遺漏了 Current-Table-Columns (清單 1) 中所示的手機資料行。

1. 比較 Current-Table-Columns 和 Bound-Recordset-Columns，以建置尚未在主要資料錄集中繫結的資料行清單 (Columns-to-Bind-Dynamically)。

   其中一個方法是在執行階段，於資料表中以平行方式迴圈處理您的資料行清單 (Current-Table-Columns)，以及已在資料錄集中繫結的資料行清單 (Bound-Recordset-Columns)。 進入 Columns-to-Bind-Dynamically 會在 Current-Table-Columns 中放置所有不會出現在 Bound-Recordset-Columns 中的名稱。

   例如，此圖顯示含一個元素的 Columns-to-Bind-Dynamically (清單 3)：在 Current-Table-Columns (清單 1) 中找到，但不在 Bound-Recordset-Columns (清單 2) 中的手機資料行。

1. 建置 Dynamic-Column-Values 清單 (如圖中的清單 4)，會在其中儲存對應至要動態繫結之資料行清單 (Columns-to-Bind-Dynamically) 中所儲存的每個資料行名稱的資料值。

   此清單的元素會扮演新資料錄集欄位資料成員的角色。 它們是要繫結動態資料行的儲存位置。 如需清單的描述，請參閱[資料行清單](#_core_lists_of_columns)。

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a> 針對新的資料行提供儲存空間

接下來，針對要動態繫結的資料行設定儲存位置。 此概念是提供要用來儲存每個資料行值的清單元素。 這些儲存位置會平行處資料錄集成員變數，其會儲存一般繫結的資料行。

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>針對新的資料行 (Dynamic-Column-Values) 提供動態儲存空間

1. 建置 Dynamic-Column-Values (與 Columns-to-Bind-Dynamically 平行)，以包含每個資料行中的資料值。

   例如，此圖顯示動態資料行值 (清單 4) 具有一個元素：一個物件， `CString` 包含目前記錄的實際電話號碼： "555-1212"。

   在最常見的情況下，Dynamic-Column-Values 具有 `CString` 型別的元素。 如果您正在處理各種不同資料型別的資料行，則您需要可包含各種型別元素的清單。

上述程式的結果是兩個主要清單：包含資料行名稱的資料行和動態資料行值，包含目前記錄之資料行中的值。

> [!TIP]
> 如果新的資料行並非全都是相同的資料型別，則您可能想要額外的平行清單，其中包含以某種方式在資料行清單中定義每個對應元素之型別的項目。 (您可以在需要時針對此項目使用 AFX_RFX_BOOL、AFX_RFX_BYTE 等值。 這些常數定義于 AFXDB.H 中。H. ) 根據您代表資料行資料類型的方式挑選清單類型。

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a> 加入 RFX 呼叫以繫結資料行

最後，在 `DoFieldExchange` 函式中放置新資料行的 RFX 呼叫，藉以安排要發生的動態繫結。

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>針對新的資料行動態加入 RFX 呼叫

1. 在主要資料錄集的 `DoFieldExchange` 成員函式中，加入要迴圈處理新資料行清單 (Columns-to-Bind-Dynamically) 的程式碼。 在每個迴圈中，從 Columns-to-Bind-Dynamically 中擷取資料行名稱，以及從 Dynamic-Column-Values 中擷取資料行的結果值。 將這些項目傳遞給適用於資料行資料型別的 RFX 函式呼叫。 如需清單的描述，請參閱[資料行清單](#_core_lists_of_columns)。

在常見的情況下，於 `RFX_Text` 函式呼叫中，您會從清單中擷取 `CString` (如下列程式碼行所示)，其中 Columns-to-Bind-Dynamically 是稱為 `m_listName` 的 `CStringList`，而 Dynamic-Column-Values 是稱為 `m_listValue` 的 `CStringList`：

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

如需 RFX 函式的詳細資訊，請參閱「類別庫參考」** 中的[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)。

> [!TIP]
> 如果新的資料行都是不同的資料型別，請在您的迴圈中使用 switch 陳述式，以針對每個型別呼叫適當的 RFX 函式。

當架構在 `Open` 程序期間呼叫 `DoFieldExchange` 以將資料行繫結至資料錄集時，對靜態資料行的 RFX 呼叫會繫結那些資料行。 接著，您的迴圈會針對動態資料行重複呼叫 RFX 函式。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[記錄集：使用大型資料項目 (ODBC) ](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
