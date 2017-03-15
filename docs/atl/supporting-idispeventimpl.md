---
title: "Supporting IDispEventImpl | Microsoft Docs"
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
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, IDispEventImpl support in COM objects"
  - "BEGIN_SINK_MAP macro"
  - "event sink maps, 宣告"
  - "IDispEventImpl class, advising and unadvising"
  - "IDispEventImpl class, 宣告"
  - "SINK_ENTRY macro"
  - "型別程式庫, 匯入"
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Supporting IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 可以用來在您的 ATL 類別的連接點接收的支援。  從外部 COM 物件可讓您的類別中處理事件所引發的連接點接收。  這些連接點接收對應事件接收對應，例如，假設您的類別。  
  
 適當地實作自己的類別的連接點接收，必須完成下列步驟:  
  
-   匯入外部元件的型別程式庫。  
  
-   宣告 `IDispEventImpl` 介面  
  
-   宣告事件接收對應  
  
-   建議和 unadvise 連接點  
  
 在實作連接點接收有關的步驟都透過修改只有標頭檔 \(.h\) 完成您的類別。  
  
## 匯入型別程式庫。  
 對於您要處理的事件，您必須匯入型別程式庫的外部元件。  這個步驟會定義能夠處理的事件，並提供使用在宣告事件接收對應時的資訊。  [\#import](../preprocessor/hash-import-directive-cpp.md) 指示詞來完成這項工作。  將您要支援加入至標頭檔的每個分派介面上的必要 `#import` 指示詞線條 \(.h\) 的類別。  
  
 下列範例會匯入外部 COM 伺服器 \(`MSCAL.Calendar.7`\) 的型別程式庫:  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/CPP/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  您必須針對每個外部型別會支援的程式庫不同的 `#import` 陳述式。  
  
## 宣告 IDispEventImpl 介面  
 現在您已匯入每個分派的型別程式庫連結，您需要宣告外部元件分派介面上的個別 `IDispEventImpl` 介面。  將外部元件的 `IDispEventImpl` 介面宣告修改您的類別中宣告。  如需參數的詳細資訊，請參閱 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
 下列程式碼會宣告兩個連接點接收， `DCalendarEvents` 介面的，但是，為了類別實作的 COM 物件 `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/CPP/supporting-idispeventimpl_2.h)]  
  
## 宣告事件接收對應  
 以適當的函式可以處理的事件通知，類別必須傳送每個事件給其正確的處理常式。  這是透過宣告事件接收對應達成。  
  
 ATL 提供幾個巨集、 [BEGIN\_SINK\_MAP](../Topic/BEGIN_SINK_MAP.md)、 [END\_SINK\_MAP](../Topic/END_SINK_MAP.md)和 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY.md)，讓此對應更為容易。  標準格式如下:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `.  .  .  //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 下列範例會宣告兩個事件處理常式的事件接收對應:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/CPP/supporting-idispeventimpl_3.h)]  
  
 實作已接近完成。  最後一個步驟相關建議和 unadvising 外部介面。  
  
## 建議 Unadvising IDispEventImpl 和介面  
 最後步驟執行時會通知的方法 \(或\) 所有 unadvise 連接點在適當的時間。  必須在外部用戶端與您的物件之間的通訊之前進行建議的這可能發生。  在您的物件變成可見之前，您的物件所支援的外部元件分派介面為輸出介面進行查詢。  建立連接，並將輸出介面的參考來處理物件的事件。  這個程序稱為「說明」。  
  
 在物件完成與外部介面之後，應該通知輸出介面進行類別不再使用它們。  這個程序稱為「unadvising」。  
  
 由於 COM 物件的唯一的本質，此程序變更，詳細、執行，在實作之間。  這些詳細資料不在本主題範圍內並沒有位址。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)