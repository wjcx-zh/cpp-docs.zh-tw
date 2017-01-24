---
title: "TN053：DAO 資料庫類別的自訂 DFX 常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dfx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自訂 DFX 常式 [C++]"
  - "DAO [C++], 類別"
  - "DAO [C++], MFC"
  - "資料庫類別 [C++], DAO"
  - "DFX (DAO 記錄欄位交換) [C++]"
  - "DFX (DAO 記錄欄位交換) [C++], 自訂常式"
  - "MFC [C++], DAO 和"
  - "TN053"
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN053：DAO 資料庫類別的自訂 DFX 常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議您在新的專案使用 [OLE DB 樣板](../data/oledb/ole-db-templates.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md) 。  請在維護現有應用程式時再使用 DAO。  
  
 這個技術提示描述 DAO 資料錄欄位交換 \(DFX\) 機制。  為了協助了解在 DFX 常式發生， `DFX_Text` 函式將詳細說明的範例。  做為其他資訊來源對這個技術提示的，您可以檢查其他的個別程式碼 DFX 函式。  您盡量經常可能不需要自訂 DFX 常式，如同您可能需要自訂 RFX 常式 \(使用 ODBC 資料庫類別\)。  
  
 這個技術提示包含:  
  
-   DFX 概觀  
  
-   使用 DAO 資料錄欄位交換和動態繫結的[範例](#_mfcnotes_tn053_examples)  
  
-   [DFX 的運作方式](#_mfcnotes_tn053_how_dfx_works)  
  
-   [知道您的自訂處理常式 DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
-   [DFX\_Text 詳細資料](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **DFX 概觀**  
  
 DAO 資料錄欄位交換機制 \(DFX\) 是用來簡化擷取和更新資料的程序，在使用 `CDaoRecordset` 類別時。  使用 `CDaoRecordset` 類別，資料成員流程簡化。  藉由衍生自 `CDaoRecordset`，您可以將資料成員加入至表示資料表或查詢的衍生類別中每個欄位。  這個「靜態繫結」機制很簡單，不過，它可能不是資料擷取\/更新選取的所有應用程式的。  每次變更， DFX 擷取每個繫結欄位目前資料錄。  如果您開發不需要擷取每個欄位的重視效能的應用程式變更時，這些貨幣， 「動態繫結」透過 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue` 可能為選取的資料存取方法。  
  
> [!NOTE]
>  DFX 和動態繫結不會互斥，因此，可以使用靜態和動態繫結的混合使用。  
  
 **範例 1 \- 至 DAO 只資料錄欄位交換的用途**  
  
 \(假設 `CDaoRecordset` 衍生類別已經開啟的 `CMySet` \)。  
  
```  
// Add a new record to the customers table  
myset.AddNew();  
myset.m_strCustID = _T("MSFT");  
myset.m_strCustName = _T("Microsoft");  
myset.Update();  
```  
  
 **範例 2 \- 僅為動態繫結的用途**  
  
 使用 `CDaoRecordset` 類別，則為 `rs`，否則為 \(假設，因此，它已經開啟\)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 ( _T("MSFT"), VT_BSTRT );  
//Note: VT_BSTRT flags string type as ANSI, instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"), VT_BSTRT );  
rs.AddNew();  
rs.SetFieldValue(_T("Customer_ID"), varFieldValue1);  
rs.SetFieldValue(_T("Customer_Name"), varFieldValue2);  
rs.Update();  
```  
  
 **範例 3 \- 至 DAO 資料錄欄位交換和動態繫結的用途**  
  
 \(假設瀏覽與 `CDaoRecordset`的員工資料衍生類別 `emp`\)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();  
  
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
   emp.GetFieldValue(_T("photo"), varPhoto);  
  
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName, varPhoto);  
```  
  
 **DFX 的運作方式**  
  
 DFX 機制工作對 MFC 使用資料錄欄位交換 \(RFX\) 機制 ODBC 來分類。  RFX 和 DFX 準則都相同，但有許多內部差異。  DFX 函式的設計是這類實際上所有程式碼一直到各自的 DFX 常式共用。  在最高層級的 DFX 只做若等事件。  
  
-   DFX 在必要時，建構 SQL 子句 **SELECT** 和 **PARAMETERS** SQL 子句。  
  
-   DAO DFX 建構的 `GetRows` 函式使用的繫結結構 \(多個之後此\)。  
  
-   DFX 處理所使用的資料緩衝區偵測變更欄位 \(如果使用雙重緩衝區\)  
  
-   DFX 在必要時，處理 **NULL** 和 **DIRTY** 狀態陣列和值設定在更新。  
  
 在 DFX 機制中心是 `CDaoRecordset` 衍生類別的 `DoFieldExchange` 函式。  這個函式會呼叫適當的作業型別的個別 DFX 函式。  在呼叫 `DoFieldExchange` 之前內部 MFC 函式作業類型。  下列清單會顯示各種作業類型和簡短說明。  
  
|作業|說明|  
|--------|--------|  
|**AddToParameterList**|組建參數子句|  
|**AddToSelectList**|組建 select 子句|  
|**BindField**|設定繫結結構|  
|**BindParam**|設定參數值。|  
|**修復**|設定內容狀態無效|  
|**AllocCache**|設定為廢棄檢查快取|  
|**StoreField**|儲存目前資料錄快取|  
|**LoadField**|還原快取到成員值|  
|**FreeCache**|可用的快取|  
|`SetFieldNull`|將欄位設定為 null & 狀態值|  
|**MarkForAddNew**|標記為已變更的欄位，如果沒有虛擬空間。|  
|**MarkForEdit**|如果不要符合快取，標記為已變更的欄位。|  
|**SetDirtyField**|設定如變更標記的欄位值。|  
  
 在下一節中，每個作業為 `DFX_Text`將詳細說明。  
  
 若要了解的重要功能如需 DAO 資料錄欄位交換程序是使用 `CDaoRecordset` 物件的 `GetRows` 函式。  DAO `GetRows` 函式可以使用數種方式。  這個技術提示簡單地只會描述 `GetRows` ，它在範圍這個技術提示之外。  
  
 DAO `GetRows` 可以用數種方式。  
  
-   它可以一次擷取多個資料錄和多個資料欄位。  這允許與處理大型資料結構和對每個欄位的適當位移的複雜性更快速的資料存取和資料每筆記錄在結構中。  MFC 不使用這個多個記錄擷取的機制。  
  
-   `GetRows` 可運作的另一種方式是讓程式設計人員為每一個欄位被擷取的資料一筆資料錄的指定繫結位址。  
  
-   DAO 「回呼至可變長度的資料列呼叫程式中以便也會允許呼叫端配置記憶體。  這第二個功能有最小化份數資料以及允許資料直接儲存的優點的類別 \( `CDaoRecordset` 衍生類別\) 的成員。  這個第二個機制是 MFC 使用方法繫結至資料之 `CDaoRecordset` 衍生類別的成員。  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> 知道您的自訂處理常式 DFX  
 從這個討論是資訊清單中所有 DFX 函式實作的最重要的作業必須是能夠設定必要資料結構成功呼叫 `GetRows`。  有許多其他作業 DFX 函式必須支援，不過，沒有相同的重要或複雜像正確指定 `GetRows` 呼叫的準備工作。  
  
 使用 DFX 線上文件中描述。  基本上，有兩個要求。  首先，成員必須加入至每個欄位和參數的 `CDaoRecordset` 衍生類別。  在這個 `CDaoRecordset::DoFieldExchange` 之後應該覆寫。  請注意這個成員的資料型別是很重要的。  它應該符合欄位的資料庫的或至少可以轉換為該型別。  例如在資料庫中的一個數字欄位，例如長整數，永遠可以轉換成文字和繫結至 `CString` 成員，不過，資料庫的文字欄位可能必須轉換為數值表示，例如長整數和繫結至一個長整數成員。  DAO 和 Microsoft Jet 資料庫引擎對轉換負責 \(而非 MFC\)。  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX\_Text 詳細資料  
 如前所述，最好的方式解譯 DFX 的運作方式是透過工作範例。  因此通過 `DFX_Text` internals 應該相當適合有助於提供對 DFX 上至少有基本的了解。  
  
 **AddToParameterList**  
 這個作業建立 Jet \("`Parameters <param name>, <param type> ... ;`"\) 所需的 SQL **PARAMETERS** 子句。  每個參數的名稱和型別 \(在 RFX 呼叫所指定\)。  如需函式 **CDaoFieldExchange::AppendParamType** 函式的個別型別的名稱。  在 `DFX_Text`的情況下，使用的型別為 `text`。  
  
 **AddToSelectList**  
 建立 SQL **SELECT** 子句。  這是相當簡單，因為 DFX 呼叫指定的資料行名稱附加 \("`SELECT <column name>, ...`"\)。  
  
 **BindField**  
 最複雜作業。  如先前是這個 `GetRows` 使用的 DAO 繫結結構所設定的位置。  您可以從 `DFX_Text` 中的程式碼看到資訊類型在結構中的 DAO 型別使用了 \(**DAO\_CHAR** 或 **DAO\_WCHAR** 在 `DFX_Text`的情況下\)。  此外，使用的繫結型別也會設定。  在較早的部分 `GetRows` 只簡單說明了，不過，解譯即可使用 MFC 的繫結型別一定是直接位址的繫結 \(**DAOBINDING\_DIRECT**\)。  此外為可變長度的資料繫結 \(如 `DFX_Text`\) 回呼繫結使用，以便 MFC 可控制記憶體配置和指定正確的長度的位址。  這個所表示是 MFC 一定會呼叫 DAO 「放置資料，因此允許直接繫結至成員變數的地方。  繫結結構的其餘部分會像記憶體配置回呼函式和資料行繫結型別的位址的事填入 \(繫結至由資料行名稱\)。  
  
 **BindParam**  
 這是呼叫中的參數成員指定參數值的 `SetParamValue` 的簡單作業。  
  
 **Fixup**  
 填入每個欄位的 **NULL** 狀態。  
  
 `SetFieldNull`  
 這項作業只表示每個欄位狀態成 **NULL** 並將成員變數值對 **PSEUDO\_NULL**。  
  
 **SetDirtyField**  
 呼叫每一個欄位標記為已變更的 `SetFieldValue` 。  
  
 所有剩餘作業只處理使用資料快取。  資料快取是資料的額外緩衝區在用來判斷事情更簡單的目前資料錄的。  例如， 「可以自動偵測 Dirty」欄位。  正如線上文件所描述可以關閉完全或在特定層級。  緩衝區的實作將對應。  這個對應來動態地配合配置的資料複本與「繫結」欄位 \(或衍生自 `CDaoRecordset` 的資料成員\) 的位址。  
  
 **AllocCache**  
 動態設定快取的欄位值並將它加入至對應。  
  
 **FreeCache**  
 刪除快取的欄位值並從對應中移除。  
  
 **StoreField**  
 複製目前欄位值至資料快取。  
  
 **LoadField**  
 複製快取的值輸入欄位成員。  
  
 **MarkForAddNew**  
 檢查目前欄位值是否在必要時，是非**NULL** 和將它標記為已變更。  
  
 **MarkForEdit**  
 與資料變更快取和標記的比較目前欄位值，如果必要的話。  
  
> [!TIP]
>  模型中現有的 DFX 常式的自訂 DFX 常式標準資料型別的。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)