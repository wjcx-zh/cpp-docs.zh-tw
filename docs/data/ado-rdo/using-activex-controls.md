---
title: "使用 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 關於 ActiveX 控制項"
  - "控制項 [C++], ActiveX"
ms.assetid: 33442173-205d-492f-82c8-9a8105358ec6
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 ActiveX 控制項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節的主題提供了使用 ActiveX 控制項的概觀。  
  
 ActiveX 控制項為 COM 元件，可支援保存性 \(Persistence\)、連接點 \(Connection Point\) 和裝載的相關標準介面。  這些標準介面定義如何將控制項裝載於控制項容器 \(Control Container\)、Exchange 訊息和處理事件的通訊協定 \(Protocol\)。  
  
 對 COM 伺服器而言，ActiveX 控制項有下列內容。  
  
|詞彙|說明|  
|--------|--------|  
|屬性|控制項擁有成員變數 \(Member Variable\)，可代表其內部狀態並實作成 **Get** 和 `Set` 存取子 \(Accessor\) 函式。  每個存取子方法都會產生 **Get** 函式，並有 propget 標記 \(Tag\) 放在 .idl 檔內。  每個存取子方法都會產生 `Set` 函式，並包含 propput 或 propputref IDL 標記。<br /><br /> 使用[包裝函式類別](../../data/ado-rdo/wrapper-classes.md)或 [OLE\/COM 物件檢視器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)來決定如何定義存取子函式。|  
|方法|控制項的行為是由其公用方法所定義。  包裝函式類別 \(Wrapper Class\) 可讓您存取控制項的方法。<br /><br /> 如果您沒有使用包裝函式類別 \(預設值\)，可藉由取得介面的指標來存取控制項的方法。<br /><br /> 公用方法的範例為 ADO 資料控制項內的 **Refresh** 方法，它可更新所擷取到的資料列集 \(Rowset\)。|  
|事件|控制項可產生一個事件，來通知主機發生某事件。  範例為 Button 控制項的 `OnClick` 事件。  當您按一下按鈕時，該按鈕會產生一個 `OnClick` 事件。  如果控制項的主機擁有該事件的處理常式，就會執行它。|  
|型別程式庫|型別程式庫會通知控制項容器有關控制項所支援的屬性、方法和事件。  型別程式庫可以以個別的檔案 \(具有 .tlb 副檔名\) 而存在或位於控制項內部。<br /><br /> 型別程式庫也包含了控制項的 coclass 資訊。  所謂的 coclass 是指以 GUID 來識別的 COM 類別。  一個 coclass 包含由控制項定義的一個或多個介面。<br /><br /> 若要檢查型別程式庫，請使用 [OLE\/COM 物件檢視器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)。|  
  
 下面主題會說明 ActiveX 控制項的用法：  
  
-   [將控制項插入 Visual C\+\+ 應用程式](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)  
  
-   [包裝函式類別](../../data/ado-rdo/wrapper-classes.md)  
  
-   [建立資料庫連接](../../data/ado-rdo/creating-database-connections.md)  
  
-   [在設計階段設定控制項屬性](../../data/ado-rdo/setting-control-properties-at-design-time.md)  
  
-   [在 ActiveX 控制項設定事件處理常式](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [修改控制項的執行階段行為](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)  
  
-   [轉散發控制項](../../data/ado-rdo/redistributing-controls.md)  
  
## 請參閱  
 [資料繫結控制項 \(ADO 和 RDO\)](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)