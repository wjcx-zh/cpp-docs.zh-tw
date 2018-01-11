---
title: "資料錄集： 動態地繫結資料行 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e834820266e83d2c07bbe46f07e2ac48b0d18e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>資料錄集：動態地繫結資料行 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 資料錄集管理您在設計階段指定的繫結資料行，但一些情況下您可能想要在設計階段不知道您的資料行繫結。 本主題說明：  
  
-   [當您可能想要將資料行以動態方式的繫結至資料錄集](#_core_when_you_might_bind_columns_dynamically)。  
  
-   [如何在執行階段動態地繫結資料行](#_core_how_to_bind_columns_dynamically)。  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，不建議您使用通常所述的技巧。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a>當您可能會動態繫結資料行  
 在設計階段，MFC 應用程式精靈或[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(從**加入類別**) 建立根據已知的資料表和資料來源上的資料行的資料錄集類別。 您設計並更新您的應用程式在執行階段使用這些資料表和資料行時，可以變更資料庫。 您或其他使用者可能會加入或卸除的資料表或加入或卸除資料行，從您的應用程式資料錄集所依賴的資料表。 這可能不是問題的所有資料存取應用程式，但如果它適用於您，如何可以您來處理資料庫結構描述，而不是重新設計，並重新編譯中的變更嗎？ 本主題的目的是為了回答這個問題。  
  
 本主題說明最常見的情況，您可能會動態繫結資料行，即開始與已知的資料庫結構描述為基礎的資料錄集，您想要在執行階段處理額外的資料行。 本主題進一步假設的額外資料行對應至`CString`欄位資料成員，最常見的情況下，雖然有提供建議來協助您管理其他資料型別。  
  
 您可以使用少量的額外的程式碼：  
  
-   [判斷哪些資料行可用在執行階段](#_core_how_to_bind_columns_dynamically)。  
  
-   [其他資料行繫結至您的資料錄集，以動態方式在執行階段](#_core_adding_the_columns)。  
  
 資料錄集仍會包含在設計階段所知的資料行的資料成員。 它也包含少量的額外的程式碼以動態方式決定任何新資料行是否已新增至您的目標資料表並，若是如此，繫結這些新的資料行以動態方式配置的儲存體 （而不是資料錄集的資料成員）。  
  
 本主題並未涵蓋其他動態繫結案例，例如卸除之資料表或資料行。 針對這些情況下，您需要更直接使用 ODBC API 呼叫。 如需資訊，請參閱 ODBC SDK*程式設計人員參考*MSDN Library CD 上。  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a>如何動態繫結資料行  
 動態繫結資料行，您必須知道 （或能夠決定） 的其他資料行的名稱。 您也必須將存放裝置配置額外的欄位資料成員、 指定其名稱和其類型，並且指定您要加入的資料行數目。  
  
 下列討論提到兩個不同的資料錄集。 第一個是主要資料錄集的目標資料表中選取的記錄。 第二個是用來在目標資料表中取得欄位的相關資訊的特殊資料行資料錄集。  
  
###  <a name="_core_the_general_process"></a>一般程序  
 最一般的層級，請遵循下列步驟：  
  
1.  建構主要資料錄集物件。  
  
     （選擇性） 將指標傳遞至開啟`CDatabase`或能提供連接資訊給其他方法中的資料行資料錄集物件。  
  
2.  採取步驟，以動態方式加入資料行。  
  
     加入下列資料行中所述的程序，請參閱。  
  
3.  開啟您的主要資料錄集。  
  
     資料錄集選取記錄，並使用資料錄欄位交換 (RFX) 繫結的靜態資料行 （其對應至資料錄集欄位資料成員） 和動態資料行 （對應至您所配置的額外儲存空間）。  
  
###  <a name="_core_adding_the_columns"></a>加入資料行  
 動態地繫結加入資料行，在執行階段需要下列步驟：  
  
1.  在執行階段決定的資料行是目標資料表中。 因為您的資料錄集類別的設計已加入至資料表的資料行的清單擷取該資訊。  
  
     一個好的方法是使用設計來查詢目標資料表 （例如資料行名稱和資料類型） 的資料行資訊的資料來源的資料行資料錄集類別。  
  
2.  提供儲存為新的欄位資料成員。 因為您的主要資料錄集類別沒有欄位資料成員的未知資料行，您必須提供一個位置來儲存名稱、 結果值，以及可能的資料類型資訊 （如果資料行不同的資料類型）。  
  
     其中一個方法是建置一或多個動態清單、 一個用於新的資料行名稱，另一個其結果值，以及協力廠商針對其資料類型 （如有必要）。 這些清單中，特別是值清單中，提供資訊和繫結必要的儲存體。 下圖說明建立清單。  
     ![建置動態繫結的資料行的清單](../../data/odbc/media/vc37w61.gif "vc37w61")  
動態繫結的資料行的建築清單  
  
3.  主要資料錄集的加入 RFX 函式呼叫`DoFieldExchange`函式，每個加入資料行。 這些 RFX 呼叫會執行擷取記錄，包括其他的資料行，以及資料行繫結至資料錄集資料成員，或您以動態方式提供的儲存體，工作。  
  
     其中一個方法是將迴圈加入至您主要資料錄集的`DoFieldExchange`執行迴圈，您的新資料行中每個資料行清單中呼叫適當的 RFX 函式清單的函式。 在每個 RFX 呼叫時，請從 [資料行名稱] 清單和儲存體中的位置相對應的結果值清單的成員傳遞的資料行名稱。  
  
###  <a name="_core_lists_of_columns"></a>資料行的清單  
 您需要使用四個清單會顯示下表中。  
  
 **目前資料表的資料行 (清單 1 圖中)**目前在資料來源上的資料表中的資料行清單。 這份清單可能符合目前繫結資料錄集中的資料行的清單。  
  
 **繫結資料錄集的資料行 (在圖例中的清單 2)**  
 資料錄集，繫結的資料行清單。 這些資料行已經有 RFX 陳述式您`DoFieldExchange`函式。  
  
 **資料行至-動態繫結 (清單 3 圖中)**  
 資料表中，但不是在資料錄集的資料行的清單。 這些是您想要動態地繫結的資料行。  
  
 **動態資料行值 (在圖例中的清單 4)**  
 包含儲存之值的清單擷取自您動態繫結資料行。 此清單的項目對應於資料行至-動態繫結，一對一。  
  
###  <a name="_core_building_your_lists"></a>建立您的清單  
 了解一般策略，您可以開啟詳細資料。 本主題的其餘部分中的程序說明如何建立顯示在清單[列出的資料行](#_core_lists_of_columns)。 程序會引導您：  
  
-   [決定不在資料錄集的資料行名稱](#_core_determining_which_table_columns_are_not_in_your_recordset)。  
  
-   [提供動態的存放裝置新增至資料表的資料行](#_core_providing_storage_for_the_new_columns)。  
  
-   [新的資料行以動態方式加入 RFX 呼叫](#_core_adding_rfx_calls_to_bind_the_columns)。  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a>決定不在資料錄集的資料表資料行  
 建立包含一份已繫結到您的主要資料錄集的資料行的清單 （繫結的資料錄集的資料行，如圖中的清單 2 所示）。 然後建立清單 （資料行至-動態繫結，衍生自目前資料表的資料行和繫結資料錄集資料行） 包含在資料來源的資料表中，但不在主要資料錄集的資料行名稱。  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>若要判斷資料行不在資料錄集 （資料行至-動態繫結） 的名稱  
  
1.  建置已繫結到您的主要資料錄集的資料行清單 （繫結的資料錄集的資料行）。  
  
     其中一個方法是在設計階段建立繫結資料錄集資料行。 您可以視覺化方式檢查 RFX 函式呼叫，在資料錄集的`DoFieldExchange`函式可取得這些名稱。 然後，將您的清單設定為使用名稱初始化陣列。  
  
     例如，圖例會顯示繫結資料錄集的資料行 (清單 2) 具有三個元素。 繫結資料錄集資料行遺漏 Phone 資料行目前資料表的資料行 (清單 1) 所示。  
  
2.  比較目前的資料表資料行和繫結資料錄集資料行來建立主要資料錄集尚未繫結的資料行 （資料行至-動態繫結） 清單。  
  
     其中一個方法是在執行的階段 （目前資料表的資料行） 和您已經以平行方式繫結 （繫結的資料錄集的資料行） 資料錄集中的資料行的清單執行迴圈的資料表中的資料行清單。 資料行繫結的動態繫放置任何名稱在目前資料表的資料行不會出現在 繫結資料錄集資料行中。  
  
     例如下, 圖顯示資料行至-動態繫結 (清單 3) 含有一個項目： 在目前資料表的資料行 (清單 1)，但不是會在繫結資料錄集的資料行 (清單 2) 中找到的 Phone 資料行。  
  
3.  建立動態資料行值 （如同在圖例中的清單 4) 的清單，用來儲存資料值會對應至每個資料行名稱是儲存在您要動態地繫結的資料行的清單 （資料行至-動態繫結）。  
  
     這份清單的項目播放的欄位資料成員的新資料錄集的角色。 它們是動態的資料行所繫結的儲存位置。 如需描述的清單，請參閱[列出的資料行](#_core_lists_of_columns)。  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a>提供新的資料行的儲存體  
 接下來，設定動態繫結的資料行的儲存位置。 這個概念是要提供用來儲存每個資料行值的清單項目。 這些儲存體位置平行儲存一般繫結的資料行的資料錄集成員變數。  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>提供動態的儲存體給新的資料行 （動態資料行值）  
  
1.  建置動態資料行值，平行資料行至-動態繫結，以包含每個資料行中的資料值。  
  
     例如下, 圖會顯示動態資料行值 (清單 4) 含有一個項目：`CString`物件，其中包含目前記錄的實際的電話號碼:"555-1212"。  
  
     在最常見的情況下，動態資料行值具有類型的項目`CString`。 如果您正在處理不同資料類型的資料行，則需要可以包含各種類型的項目清單。  
  
 前述程序的結果是兩個主要的清單： 資料行至-動態繫結包含名稱的資料行和動態資料行值包含目前記錄的資料行中的值。  
  
> [!TIP]
>  如果新的資料行不是所有相同的資料類型，您可能需要額外的平行清單包含的每個對應的項目類型定義的資料行清單中的項目。 (您可以使用值**AFX_RFX_BOOL**， **AFX_RFX_BYTE**，依此類推，如果您想。 這些常數 AFXDB 中定義。H.)選擇清單類型，根據您如何表示資料行資料類型。  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a>繫結資料行加入 RFX 呼叫  
 最後，安排發生放入 RFX 呼叫新的資料行中的動態繫結您`DoFieldExchange`函式。  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>若要以動態方式加入 RFX 呼叫新的資料行  
  
1.  您主要資料錄集中`DoFieldExchange`成員函式中，新增您新的資料行 （資料行至-動態繫結） 的清單執行迴圈的程式碼。 在每個迴圈中，擷取資料行名稱與資料行至-動態繫結的動態資料行值的資料行的結果值。 傳遞 RFX 函式呼叫的這些項目適用於資料行的資料類型。 如需描述的清單，請參閱[列出的資料行](#_core_lists_of_columns)。  
  
 在常見的情況下，在您`RFX_Text`函式會呼叫您擷取`CString`物件的清單中，如同下列程式碼，其中資料行至-動態繫結是從`CStringList`呼叫`m_listName`和動態資料行值是`CStringList`呼叫`m_listValue`:  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 如需 RFX 函式的詳細資訊，請參閱[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*類別庫參考*。  
  
> [!TIP]
>  如果新的資料行不同的資料類型，請使用 switch 陳述式在迴圈中呼叫適當的 RFX 函式每一種類型。  
  
 架構會呼叫時`DoFieldExchange`期間**開啟**靜態資料行繫結的資料行，將資料行繫結至資料錄集，RFX 呼叫的程序。 然後您迴圈重複呼叫 RFX 函式的動態資料行。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：使用大型的資料項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)