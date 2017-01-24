---
title: "對話方塊資料交換 | Microsoft Docs"
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
  - "取消資料交換"
  - "擷取使用者輸入"
  - "CDataExchange 類別, 使用 DDX"
  - "DDX (對話資料交換), 取消"
  - "DDX (對話資料交換), 資料交換機制"
  - "對話方塊資料"
  - "對話方塊資料, 擷取"
  - "對話方塊, 資料交換"
  - "對話方塊, 初始化"
  - "對話方塊, 使用 DDX 擷取使用者輸入"
  - "DoDataExchange 方法"
  - "初始化對話方塊"
  - "擷取對話方塊資料"
  - "傳輸對話方塊資料"
  - "UpdateData 方法"
  - "使用者輸入, 從 MFC 對話方塊擷取"
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對話方塊資料交換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您使用 DDX 機制，通常您會將對話方塊物件成員變數的初始值設定在 `OnInitDialog` 處理常式或對話方塊建構函式中。  在對話方塊顯示之前，框架的 DDX 機制將成員變數的值傳送至對話方塊的控制項，當對話方塊顯示時它們會出現，已回應 `DoModal` 或 **Create**。  `CDialog` 的 `OnInitDialog` 的預設實作會呼叫類別 `CWnd` 的 `UpdateData` 成員函式，來初始化對話方塊中的控制項。  
  
 當使用者按一下確定按鈕時 \(或者每當您使用引數 **TRUE** 呼叫 `UpdateData` 成員函式時\)，同一個機制會將值從控制項傳送至成員變數。  對話資料驗證機制會驗證您指定驗證規則的所有資料項目。  
  
 下圖說明對話資料交換。  
  
 ![對話方塊資料交換](../mfc/media/vc379d1.png "vc379D1")  
對話資料交換  
  
 `UpdateData` 可用於雙向，如 **BOOL** 參數傳遞給它所指定的。  若要執行交換，`UpdateData` 會使用 `CDataExchange` 物件並呼叫您對話方塊類別的 `CDialog` `DoDataExchange` 成員函式的覆寫。  `DoDataExchange` 會採用型別 `CDataExchange`的引數。  傳遞至 `UpdateData` 的 `CDataExchange` 物件表示交換的內容，定義資訊，例如交換的方向。  
  
 當您 \(或程式碼精靈\) 覆寫 `DoDataExchange` 時，請指定每個資料成員 \(控制項\) 的 DDX 函式的呼叫。  每個 DDX 函式根據 `UpdateData` 傳遞給 `DoDataExchange` 的 `CDataExchange` 引數所提供之內容，知道如何雙向的交換資料。  
  
 MFC 提供許多 DDX 函式，以進行不同種類的交換。  下列範例顯示呼叫兩個 DDX 函式和一個 DDV 函式的 `DoDataExchange` 覆寫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/CPP/dialog-data-exchange_1.cpp)]  
  
 `DDX_` 和 `DDV_` 這些行是資料映像。  這個範例 DDX 和 DDV 函式分別為核取方塊控制項和編輯方塊控制項。  
  
 如果使用者取消強制回應對話方塊，`OnCancel` 成員函式會結束對話方塊，並且 `DoModal` 傳回值 **IDCANCEL**。  在這種情況下，對話方塊和對話方塊物件之間不會有資料交換。  
  
## 請參閱  
 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [對話方塊資料驗證](../mfc/dialog-data-validation.md)