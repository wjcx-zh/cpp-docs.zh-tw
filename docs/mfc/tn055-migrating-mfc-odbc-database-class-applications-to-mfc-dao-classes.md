---
title: "TN055：將 MFC ODBC 資料庫類別應用程式移轉至 MFC DAO 類別 | Microsoft Docs"
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
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 移轉"
  - "移轉資料庫應用程式"
  - "移轉 ODBC 資料庫應用程式"
  - "移轉 [C++], ODBC 資料庫應用程式"
  - "ODBC [C++], DAO"
  - "ODBC 類別 [C++], DAO 類別"
  - "將資料庫應用程式移植到 DAO"
  - "將 ODBC 資料庫應用程式移植到 DAO"
  - "TN055"
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN055：將 MFC ODBC 資料庫類別應用程式移轉至 MFC DAO 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議您針對新的專案使用[OLE DB 樣板](../data/oledb/ole-db-templates.md)或是 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md) 。  請在維護現有應用程式時再使用 DAO。  
  
 **概觀**  
  
 在大部分情況下移轉使用 MFC 的 ODBC 資料庫類別對 MFC 的 DAO 資料庫類別的應用程式可能是需要的。  這個技術提示將詳述大多 MFC ODBC 和 DAO 類別之間的差異。  如果需要考慮到差異，從移轉至 ODBC 類別的應用程式加入至 MFC 類別應該不困難。  
  
 **為何要從 ODBC 移轉至 DAO?**  
  
 有許多原因。您可能想要將 ODBC 資料庫類別至 DAO 資料庫類別，不過，這項決定不一定是簡單或明顯。  要記住的一件事是 DAO 使用的 Microsoft Jet 資料庫引擎無法讀取您擁有 ODBC 驅動程式的 ODBC 資料來源。  可能更有效率使用 ODBC 資料庫類別或直接呼叫 ODBC ，不過， Microsoft Jet 資料庫引擎可以讀取 ODBC 資料。  
  
 ODBC\/DAO 容易做出決策的一些簡單的案例。  例如，當您在 Microsoft Jet 機引擎可直接讀取的格式只需要對資料的存取 \(存取格式， Excel 格式等等\)，資訊清單的選項是使用 DAO 資料庫類別。  
  
 當您的資料出現在伺服器或於各種不同的伺服器，更複雜的案例來了。  在這種情況下，使用 ODBC 資料庫類別或 DAO 資料庫類別的決定是困難的。  如果您要執行動作，如異質聯結 \(聯結將資料從伺服器在如 SQL Server 和 Oracle 的多種格式\)，則 Microsoft Jet 資料庫引擎執行聯結而非強制您完成必要的工作您是否使用了 ODBC 資料庫類別或直接呼叫 ODBC。  如果您使用支援驅動程式游標的 ODBC 驅動程式，您的最佳選擇可能是 ODBC 資料庫類別。  
  
 索引可能會很複雜，因此，您可能要撰寫一些範例程式碼來測試指定的各種方法效能的特殊需求。  這個技術提示假設您做出這項決定是從 ODBC 資料庫類別移轉至 DAO 資料庫類別。  
  
 **在 ODBC 資料庫類別和 MFC DAO 資料庫類別之間的相似處**  
  
 MFC ODBC 類別的原始設計根據使用 Microsoft Access 和 Microsoft Visual Basic 的 DAO 物件模型。  這表示有 ODBC 和 MFC DAO 類別的許多常見功能，在區段中不會列出所有。  一般而言，程式設計模型是相同的。  
  
 反白顯示一些相似:  
  
-   ODBC 和 DAO 類別會使用基礎資料庫管理系統的資料庫物件 \(DBMS\)。  
  
-   兩個具有代表一組結果的資料錄集物件從一個 DBMS 傳回。  
  
-   DAO 資料庫和資料錄集物件有幾乎和 ODBC 類別完全相同的成員。  
  
-   兩組類別，擷取資料的程式碼是弧形，除了一些物件和成員的名稱變更。  需要變更，不過，通常處理的方式相當直接變更，當轉換成從 ODBC 類別 DAO 類別時。  
  
 例如，在兩個模型擷取資料的程序是建立並開啟資料庫物件，建立及開啟資料錄集物件，並透過巡覽 \(移動\) 執行特定作業的資料。  
  
 **ODBC 和 DAO MFC 類別間的差異**  
  
 DAO 類別包含多個物件和一組豐富的方法，不過，這個部分只會詳細說明相似的類別和功能的差異。  
  
 可能類別之間最明顯的差異是類似的類別和全域函式的名稱。  下列清單顯示物件、方法或全域函式的名稱與資料庫類別:  
  
|類別或函式。|在 MFC DAO 類別的對等用法|  
|------------|-----------------------|  
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
|**RFX\_Date \***|**DFX\_Date** \(以`COleDateTime`為基礎\)。|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \* `RFX_Date` 函式會根據 `CTime` 和 **TIMESTAMP\_STRUCT**。  
  
 可能會影響應用程式並要求得更多的功能的主要變更比簡單名稱變更如下所示。  
  
-   使用的常數和巨集指定與資料錄集的事開啟型別，而且變更資料錄集開啟選項。  
  
     使用 ODBC 將必要的 MFC 類別透過巨集或列舉型別定義這些選項。  
  
     DAO 類別， DAO 提供這些選項的定義在標頭檔 \(DBDAOINT.H\)。  因此資料錄集類型是 `CRecordset`的一個列舉的成員，不過，DAO 它是常數。  例如您會使用 **snapshot** ，當指定 `CRecordset` 的型別，但在 ODBC **DB\_OPEN\_SNAPSHOT** 時，指定 `CDaoRecordset`的型別。  
  
-   `CRecordset` 的預設資料錄集類型是 **snapshot** ，在 `CDaoRecordset` 的預設資料錄集類型是 **dynaset** 時 \(如需 ODBC 類別快照中的其他問題。請參閱下面的注意事項\)。  
  
-   ODBC `CRecordset` 類別可以選擇建立一個順向資料錄集類型。  在 `CDaoRecordset` 類別，不是順向資料錄集類型，而是屬性 \(或選項\) 資料錄集的特定型別。  
  
-   另一個資料錄集，當開啟 `CRecordset` 物件表示的資料錄集的資料可以讀取和附加。  `CDaoRecordset` 物件，附加選項實際上是表示資料錄集的資料只能附加 \(而非讀取\)。  
  
-   ODBC 類別的交易成員函式是 `CDatabase` 的成員和在資料庫層級動作。  DAO 類別，交易成員函式是較高層級類別 \(`CDaoWorkspace`\) 的成員和可能因而影響共用同一個工作區 \(交易空間\) 的多個 `CDaoDatabase` 物件。  
  
-   變更例外狀況類別。  **CDBExceptions** 在 ODBC 類別和 **CDaoExceptions** 擲回 DAO 類別。  
  
-   當 **DFX\_Date** 使用 `COleDateTime`時，`RFX_Date` 會使用 `CTime` 和 **TIMESTAMP\_STRUCT** 物件。  `COleDateTime` 幾乎與 `CTime` 相同，但是是根據 8 個位元組的 OLE **DATE** 而不為 4 個位元組的 `time_t` ，因此它可以保存資料的一個更大的範圍。  
  
    > [!NOTE]
    >  DAO \(`CDaoRecordset`\) 是唯讀，當 ODBC \(`CRecordset`\) 時快照可能是更新根據 ODBC 資料指標程式庫的驅動程式和用途。  如果您使用資料指標程式庫， `CRecordset` 可更新的快照。  如果您使用任何從桌面驅動程式套件 3.0 的 Microsoft 驅動程式，而不使用 ODBC 資料指標程式庫， `CRecordset` 快照是唯讀的。  如果您使用其他驅動程式，請檢查驅動程式的文件檢視快照 \(**STATIC\_CURSORS**\) 是否為唯讀。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)