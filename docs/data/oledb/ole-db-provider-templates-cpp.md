---
title: "OLE DB 提供者樣板 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫 [C++], OLE DB 樣板"
  - "OLE DB 提供者樣板 (C++), 關於 OLE DB 提供者樣板"
  - "OLE DB 提供者 [C++], 關於提供者"
  - "範本 [C++], OLE DB"
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 提供者樣板 (C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 是 Microsoft 通用資料存取策略的重要部分。  OLE DB 設計可讓您對任何資料來源進行高效能資料存取。  任何表格式資料都可透過 OLE DB 來檢視，而不管它是否來自資料庫。  這種彈性提供您極大的使用能力。  
  
 如同 [OLE DB 消費者和提供者](../../data/oledb/ole-db-consumers-and-providers.md)內所述說明，OLE DB 會使用消費者和提供者 \(Provider\) 的概念。  消費者可提出資料要求；而提供者則以表格形式將資料傳回給消費者。  從程式設計觀點而言，這種模型最重要的內涵是提供者必須實作消費者可能發出的任何呼叫。  
  
## 什麼是提供者呢？  
 OLE DB 提供者 \(Provider\) 是一組可為來自消費者物件介面呼叫服務的 COM 物件，並以表格形式將資料從持久性來源 \(稱為資料存放區\) 傳輸至消費者。  
  
 提供者可以是簡單或複雜的。  提供者可支援最少量功能，或可實作更多介面的全功能生產品質之提供者。  提供者可傳回資料表，允許用戶端決定該資料表的格式，且提供者可在該資料上執行作業。  
  
 每個提供者都會實作一組標準 COM 物件來處理用戶端要求，具有任何 OLE DB 消費者都可以從任何提供者 \(無論是哪種語言，例如 C\+\+ 和 Basic\) 存取資料的標準意義。  
  
 每個 COM 物件都包含多個介面，有些是必要的，有些則是選擇性 \(Optional\) 的。  透過實作強制的介面，提供者可保證提供任何用戶端都可使用的基本程度的功能 \(稱為相容性\)。  提供者可實作選擇性介面來提供其他功能。  如需這些介面的詳細資訊，請參閱 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)。  用戶端應該永遠呼叫 `QueryInterface` 來判斷提供者是否支援指定的介面。  
  
## OLE DB 規格層級支援  
 OLE DB 提供者樣板可支援 OLE DB 2.7 版規格。  透過使用 OLE DB 提供者樣板，您可實作層級 0 的相容提供者   例如，提供者範例會使用樣板實作執行 DOS DIR 命令以查詢檔案系統的非 SQL \(MS\-DOS\) 命令伺服器。  Provider 範例將以資料列集 \(Rowset\) 來傳回目錄資訊，這是傳送表格式資料的標準 OLE DB 機制。  
  
 OLE DB 樣板支援的最簡單提供者類型為不含命令的唯讀提供者。  具有命令的提供者也受支援，以及書籤和讀取 \/ 寫入功能。  您可編寫其他程式碼來實作讀取\/寫入提供者。  目前版本並不支援動態的資料列集和交易，不過您仍可視需要加入它們。  
  
## 何時需要建立 OLE DB 提供者？  
 您不需要一直建立自己的提供者，Microsoft 在 Visual C\+\+ 的 \[**資料連結屬性**\] 對話方塊中提供了數個預先封裝的標準提供者。  建立 OLE DB 提供者主要是為了運用通用資料存取策略。  採用這種做法的優點是：  
  
-   透過任何語言像是 C\+\+、Basic 和 Visual Basic Scripting Edition 來存取資料。  這點可使組織內不同的程式設計人員在不管使用哪種語言的情況下，都可使用相同的方式存取相同的資料。  
  
-   將您的資料公開給其他資料來源，例如 SQL Server、Microsoft Excel 和 Access。  這點在您要以不同格式傳送資料時非常實用。  
  
-   參與跨資料來源 \(異質性\) 作業。  這是非常有效率的資料倉儲方式。  您可透過使用 OLE DB 提供者，讓資料保持其原型格式，並仍可使用簡單作業存取。  
  
-   將其他功能加入至您的資料，例如查詢處理。  
  
-   增加存取資料的效能 \(透過控制資料操作方式\)。  
  
-   增加強固性。  如果您的資料格式僅可由一位程式設計人員存取，這將會造成危險。  透過使用 OLE DB 提供者，您可將該專有格式開放給所有的程式設計人員。  
  
## 唯讀和可更新提供者  
 提供者在複雜性和功能上有很大的差異。  將提供者分成唯讀提供者和可更新提供者兩類將會很有用：  
  
-   Visual C\+\+ 6.0 只能支援唯讀的提供者 \(Provider\)。  [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)將討論如何建立唯讀提供者。  
  
-   Visual C\+\+ .NET 支援可更新的提供者，此類提供者可更新 \(寫入\) 資料存放區。  如需可更新提供者的詳細資訊，請參閱[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)，而 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例是可更新提供者的範例。  
  
 如需詳細資訊，請參閱：  
  
-   [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)  
  
## 請參閱  
 [資料存取](../Topic/Data%20Access%20in%20Visual%20C++.md)   
 [OLE DB SDK 文件](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)