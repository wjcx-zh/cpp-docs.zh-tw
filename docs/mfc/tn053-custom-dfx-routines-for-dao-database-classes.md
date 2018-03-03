---
title: "TN053: DAO 的自訂 DFX 常式資料庫類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6935e4b3f2c8159677d1d322f6f875246160da2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 資料庫類別的自訂 DFX 常式
> [!NOTE]
>  Visual c + + 環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 呤魽您畷樾[OLE DB 樣板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO 中維護現有應用程式。  
  
 這個技術提示描述 DAO 資料錄欄位交換 (DFX) 機制。 若要協助您了解為什麼在 DFX 常式中，`DFX_Text`函式將說明在做為範例的詳細資料。 為這個技術提示資訊的其他來源，您可以檢查程式碼的其他個別的 DFX 函式。 您可能不需要自訂 DFX 常式視您可能需要自訂 RFX 常式 （搭配 ODBC 資料庫類別）。  
  
 這個技術提示包含：  
  
-   DFX 概觀  
  
- [範例](#_mfcnotes_tn053_examples)使用 DAO 資料錄欄位交換和動態繫結  
  
- [DFX 的運作方式](#_mfcnotes_tn053_how_dfx_works)  
  
- [自訂 DFX 常式的功能](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [DFX_Text 的詳細資料](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **DFX 概觀**  
  
 DAO 資料錄欄位交換 (DFX) 機制用來簡化擷取和更新資料時使用的程序`CDaoRecordset`類別。 使用資料成員的簡化程序`CDaoRecordset`類別。 由衍生自`CDaoRecordset`，您可以加入代表資料表或查詢中的每個欄位的衍生類別中的資料成員。 這項 「 靜態繫結 」 機制很簡單，但是它可能無法選擇的所有應用程式資料擷取/更新方法。 DFX 在每次變更目前的記錄時擷取每個繫結的欄位。 如果您正在開發效能敏感應用程式不需要變更貨幣時，擷取每個欄位的 「 動態繫結 」 透過`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`可能會選擇的資料存取方法。  
  
> [!NOTE]
>  DFX 和動態繫結不會互斥，所以可以使用靜態和動態繫結的混合式用法。  
  
## <a name="_mfcnotes_tn053_examples"></a>使用的 DAO 資料錄欄位交換只範例 1:  
  
 (假設`CDaoRecordset`-衍生的類別`CMySet`尚未開啟)  
  
```  
// Add a new record to the customers table  
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```  
  
 **只有動態的繫結的範例 2： 使用**  
  
 (假設使用`CDaoRecordset`類別`rs`，且已開啟)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```  
  
 **範例 3 — 使用的 DAO 資料錄欄位交換和動態繫結**  
  
 (假設使用的瀏覽員工資料`CDaoRecordset`-衍生的類別`emp`)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();

 
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
    emp.GetFieldValue(_T("photo"),
    varPhoto);

 
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName,
    varPhoto);
```  
  
## <a name="_mfcnotes_tn053_how_dfx_works"></a>DFX 的運作方式  
  
 DFX 機制的運作方式類似使用 MFC ODBC 類別的資料錄欄位交換 (RFX) 機制。 DFX 和 RFX 的原則是相同的但有許多內部的差異。 DFX 函式的設計是的因此幾乎所有的程式碼由個別的 DFX 常式共用。 在最高等級 DFX 只會幾件事。  
  
-   DFX 建構 SQL**選取**子句和 SQL**參數**子句如有必要。  
  
-   DFX 建構使用 DAO 的繫結結構`GetRows`函式 （更詳細的更新版本）。  
  
-   DFX 管理用來偵測已變更的欄位 （如果正在使用雙重緩衝） 的資料緩衝區  
  
-   DFX 管理**NULL**和**DIRTY**狀態陣列，並更新如有必要設定的值。  
  
 DFX 注重機制是`CDaoRecordset`衍生類別的`DoFieldExchange`函式。 此函式將呼叫分派至適當的作業類型的個別的 DFX 函式。 然後再呼叫`DoFieldExchange`內部 MFC 函式會將作業類型。 下表列出各種作業類型和簡短描述。  
  
|運算|描述|  
|---------------|-----------------|  
|**AddToParameterList**|組建參數子句|  
|**AddToSelectList**|組建的 SELECT 子句|  
|**BindField**|設定繫結結構|  
|**BindParam**|設定參數值|  
|**修復**|設定 NULL 狀態|  
|**AllocCache**|配置已變更的核取的快取|  
|**StoreField**|將目前的記錄儲存至快取|  
|**LoadField**|還原給成員值的快取|  
|**FreeCache**|釋出快取|  
|`SetFieldNull`|設定欄位的狀態 （& s） 值為 NULL|  
|**MarkForAddNew**|標記欄位中途如果不是虛擬 NULL|  
|**MarkForEdit**|如果中途的標記欄位不符合快取|  
|**SetDirtyField**|設定欄位標示為中途的值|  
  
 下一節將說明每個作業的詳細`DFX_Text`。  
  
 若要了解有關 DAO 資料錄欄位交換程序最重要的功能是它會使用`GetRows`函式的`CDaoRecordset`物件。 DAO`GetRows`函式可以數種方式運作。 這個技術提示將簡要說明`GetRows`，所以這個技術提示的範圍內。  
  
 DAO`GetRows`可以數種方式運作。  
  
-   它可以擷取多個記錄和多個欄位的資料一次。 如此可更快速的資料存取，但複雜的處理大型資料結構和適當的位移給每個欄位，以及資料結構中的每一筆記錄。 MFC 不會利用這個擷取機制的多個記錄。  
  
-   另一種方式`GetRows`可以工作可讓程式設計人員指定的每一個欄位的一筆記錄的資料擷取的資料繫結位址。  
  
-   DAO 會也 「 回呼 」 至可變長度資料行呼叫端才能讓呼叫端配置的記憶體。 此第二個功能具有的最小化的資料複本數目，以及允許直接儲存的資料成員中類別的優點 (`CDaoRecordset`衍生的類別)。 此第二種機制是用來繫結至資料成員中的 MFC 的方法`CDaoRecordset`衍生的類別。  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>自訂 DFX 常式的功能  
 很明顯來自必須能夠成功呼叫設定必要的資料結構中任何 DFX 函式實作的最重要的作業。 這個討論`GetRows`。 DFX 函式，也必須支援其他作業，但不為重要或複雜到像正確準備的許多`GetRows`呼叫。  
  
 使用 DFX 是線上文件中所述。 基本上，有兩項需求。 首先，必須新增成員至`CDaoRecordset`衍生的類別，針對每個繫結的欄位和參數。 接下來`CDaoRecordset::DoFieldExchange`應該覆寫。 請注意，成員的資料型別是很重要。 它應該符合資料庫中欄位的資料，或至少可轉換為該類型。 例如在資料庫中，例如長整數的數值欄位可以永遠轉換成文字和繫結至`CString`成員，但資料庫中的文字欄位不一定可以轉換成數值表示法，例如長整數和繫結至長 integer 成員。 DAO 和 Microsoft Jet 資料庫引擎負責轉換 （而非 MFC）。  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>DFX_Text 的詳細資料  
 如先前所述，說明 DFX 的運作方式的最佳方式是利用範例。 針對此用途的內部資訊透過`DFX_Text`應該運作相當可協助您提供的 DFX 至少有基本了解。  
  
 **AddToParameterList**  
 這項作業會建立 SQL**參數**子句 ("`Parameters <param name>, <param type> ... ;`」) 所需的 Jet。 每個參數是名為和型別 （如 RFX 呼叫中指定）。 請參閱函數**CDaoFieldExchange::AppendParamType**函式，以查看個別類型的名稱。 如果是`DFX_Text`，使用的類型是`text`。  
  
 **AddToSelectList**  
 建置 SQL**選取**子句。 這會相當直截了當 DFX 呼叫所指定的資料行名稱只是因為附加 (「`SELECT <column name>, ...`")。  
  
 **BindField**  
 最複雜的作業。 如先前所述這是 DAO 繫結結構會由`GetRows`設定。 您可以從程式碼中看到`DFX_Text`的結構中的資訊類型包括使用的 DAO 類型 (**DAO_CHAR**或**DAO_WCHAR**是`DFX_Text`)。 此外，使用繫結的型別也設定。 在前一節中`GetRows`描述僅簡單，但它是足以說明 MFC 使用的繫結的型別一定是直接定址的繫結 (**DAOBINDING_DIRECT**)。 此外可變長度資料行繫結 (例如`DFX_Text`) 回呼繫結使用，因此 MFC 可以控制記憶體配置和指定的位址是正確的長度。 這表示是 MFC 永遠可以辨識 DAO"where"放置資料，因此允許直接至成員變數繫結。 繫結結構的其餘部分會填入之類的位址的記憶體配置回呼函式和資料行繫結 （繫結資料行名稱） 的類型。  
  
 **BindParam**  
 這是簡單的作業呼叫`SetParamValue`參數成員中指定的參數值。  
  
 **修復**  
 填入**NULL**每個欄位的狀態。  
  
 `SetFieldNull`  
 這項作業只會將標示為每個欄位狀態**NULL**並將成員變數的值設定為**PSEUDO_NULL**。  
  
 **SetDirtyField**  
 呼叫`SetFieldValue`每個欄位標示為已變更。  
  
 所有其餘的作業只處理使用的資料快取。 資料快取是額外的緩衝區，用來簡化某些項目是目前記錄中的資料。 比方說，您可以自動偵測這項 「 有所變更 」 欄位。 線上文件中所述就可以關閉完全或欄位層級。 緩衝區的實作會使用對應。 此對應用來比對資料的動態配置的複本與 「 繫結 」 欄位的位址 (或`CDaoRecordset`衍生的資料成員)。  
  
 **AllocCache**  
 動態配置的快取的欄位值，並將它加入至地圖。  
  
 **FreeCache**  
 刪除快取的欄位值，並將它從對應移除。  
  
 **StoreField**  
 將目前的欄位值複製到資料快取。  
  
 **LoadField**  
 將快取的值複製到欄位成員。  
  
 **MarkForAddNew**  
 檢查目前的欄位值是否非**NULL** ，並讓其中途如有必要。  
  
 **MarkForEdit**  
 比較目前的欄位值與資料快取，並將標示為中途如有必要。  
  
> [!TIP]
>  模型標準的資料類型的現有 DFX 常式的自訂 DFX 常式。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

