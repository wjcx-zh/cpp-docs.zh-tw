---
title: "主動式文件 | Microsoft Docs"
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
  - "主動式文件 [C++]"
  - "主動式文件 [C++], 需求"
  - "主動式文件 [C++], 檢視"
  - "OLE [C++], 主動式文件"
  - "檢視物件, 需求"
  - "檢視 [C++], 主動式文件"
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 主動式文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

現用文件擴充 OLE 複合文件技術。  這些擴充功能提供以處理檢視的其他介面的形式，因此，物件可以在容器內運作，仍然保留其顯示和列印功能的控制項。  這個程序會顯示文件外部架構 \(例如 Microsoft Office Binder 或 Microsoft Internet Explorer\) 和在原生框架 \(如產品的檢視連接埠\)。  
  
 本節說明 [現用文件的要求](#requirements_for_active_documents)功能。  現用文件擁有一組資料並存取資料可以儲存和擷取的儲存區。  可以建立和管理其資料的一或多個檢視。  除了支援 OLE 文件通常內嵌和就地啟動介面之外，主動式文件傳達其透過 `IOleDocument`建立檢視。  透過這個介面，容器可以建置和 \(可能的\) 現用文件可能顯示的檢視。  透過這個介面，主動式文件也可以提供有關本身的其他資訊，例如它是否支援多個檢視或複雜的矩形。  
  
 下列是 **IOleDocument** 介面。  請注意 **IEnumOleDocumentViews** 介面 **IOleDocumentView \*** 為型別的標準 OLE 列舉值。  
  
 `interface IOleDocument : IUnknown`  
  
 `{`  
  
 `HRESULT CreateView(`  
  
 `[in] IOleInPlaceSite *pIPSite,`  
  
 `[in] IStream *pstm,`  
  
 `[in] DWORD dwReserved,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);`  
  
 `HRESULT EnumViews(`  
  
 `[out] IEnumOleDocumentViews **ppEnum,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `}`  
  
 每個現用文件必須有這個介面的檢視框架提供者。  如果文件未在容器中內嵌，主動式文件伺服程式必須提供檢視框架。  不過，當現用文件在主動式文件容器中內嵌，容器提供檢視框架。  
  
 現用文件可以建立其資料的[檢視](#requirements_for_view_objects)的一個或多個型別 \(例如，正常、大綱，頁面配置，依此類推\)。  檢視如同資料可以看到的篩選條件。  即使文件只有檢視的一種型別，您可能仍然要支援多個檢視為支援新視窗功能的方法 \(例如，在 \[**視窗**\] 功能表的 **New Window** 項目在 Office 應用程式\)。  
  
##  <a name="requirements_for_active_documents"></a> 現用文件的要求  
 在主動式文件容器可以顯示現用文件必須:  
  
-   使用 OLE 複合檔案做為它的儲存機制會實作 `IPersistStorage`。  
  
-   支援 OLE 文件基礎內嵌功能，包括 **Create From File**。  這需要介面 `IPersistFile`、 `IOleObject`和 `IDataObject`。  
  
-   支援一或多個檢視，每個都可以就地啟用。  即檢視必須支援介面 `IOleDocumentView` 以及 `IOleInPlaceObject` 和 `IOleInPlaceActiveObject` 介面 \(使用容器的 **IOleInPlaceSite** 和 **IOleInPlaceFrame** 介面\)。  
  
-   支援標準現用文件介面 `IOleDocument`、 `IOleCommandTarget`和 `IPrint`。  
  
 了解使用容器的介面決定何時以及如何在這些需求是隱含的。  
  
##  <a name="requirements_for_view_objects"></a> 檢視物件的要求  
 現用文件可以建立其一個或多個資料檢視。  功能性來說，這些像是特定方法上的連接埠所顯示的資料。  如果現用文件只支援一個檢視，使用單一類別，主動式文件和該單一檢視中實作。  **IOleDocument::CreateView** 傳回相同的物件的 `IOleDocumentView` 介面指標。  
  
 除了 `IOleDocumentView`以外，在主動式文件容器中表示，檢視元件必須支援 **IOleInPlaceObject** 和 **IOleInPlaceActiveObject** :  
  
 `interface IOleDocumentView : IUnknown`  
  
 `{`  
  
 `HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);`  
  
 `HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);`  
  
 `HRESULT GetDocument([out] IUnknown **ppunk);`  
  
 `[input_sync] HRESULT SetRect([in] LPRECT prcView);`  
  
 `HRESULT GetRect([in] LPRECT prcView);`  
  
 `[input_sync] HRESULT SetRectComplex(`  
  
 `[in] LPRECT prcView,`  
  
 `[in] LPRECT prcHScroll,`  
  
 `[in] LPRECT prcVScroll,`  
  
 `[in] LPRECT prcSizeBox);`  
  
 `HRESULT Show([in] BOOL fShow);`  
  
 `HRESULT UIActivate([in] BOOL fUIActivate);`  
  
 `HRESULT Open(void);`  
  
 `HRESULT CloseView([in] DWORD dwReserved);`  
  
 `HRESULT SaveViewState([in] IStream *pstm);`  
  
 `HRESULT ApplyViewState([in] IStream *pstm);`  
  
 `HRESULT Clone(`  
  
 `[in] IOleInPlaceSite *pIPSiteNew,`  
  
 `[out] IOleDocumentView **ppViewNew);`  
  
 `}`  
  
 每個檢視都有相關聯的檢視網站，封裝檢視框架和檢視埠 \(在該視窗的 HWND 和矩形區域\)。  這個網站所公開這個功能，透過標準 **IOleInPlaceSite** 介面。  請注意超過單一 HWND 的檢視區是可能的。  
  
 通常，檢視的每個型別都有不同列印的表示。  因此檢視和對應的檢視網站應該實作的介面，如果分別是 `IPrint` 和 `IContinueCallback`。  檢視框架必須與檢視提供者透過 **IPrint** 交涉，在列印啟動時，因此，頁首、頁尾、框線和相關項目才能正確列印。  檢視提供者透過 `IContinueCallback`通知列印相關的事件架構。  如需使用這些介面的詳細資訊，請參閱[以程式設計方式列印](../mfc/programmatic-printing.md)。  
  
 注意如果現用文件只支援一個檢視，使用單一有形類別，主動式文件和該單一檢視中來實作。  **IOleDocument::CreateView** 簡單傳回相同的物件的 `IOleDocumentView` 介面指標。  為了簡化，不需要有兩個不同的物件執行個體，而只需要一個檢視。  
  
 檢視物件也可以是命令目標。  藉由實作 `IOleCommandTarget` 檢視可以接收來自容器的使用者介面的命令 \(例如 **New**， **Open**， **Save As**，在**檔案**功能表的 **Print** ; **Copy**，**Paste**，在**編輯**功能表的**Undo**\)。  如需詳細資訊，請參閱[訊息處理和命令目標](../mfc/message-handling-and-command-targets.md)。  
  
## 請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)