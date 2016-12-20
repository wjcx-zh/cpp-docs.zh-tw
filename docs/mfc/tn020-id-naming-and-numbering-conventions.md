---
title: "TN020：ID 命名和編號慣例 | Microsoft Docs"
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
  - "vc.id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資源識別項"
  - "資源識別項, 命名及編號"
  - "TN020"
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN020：ID 命名和編號慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註說明 MFC 2.0 為資源、命令、字串、控制項和子視窗使用的 ID 編號和命名慣例。  
  
 MFC ID 編號和命名慣例不符合下列要求:  
  
-   提供跨由 Visual C\+\+ 資源編輯器支援的 MFC 程式庫和 MFC 應用程式使用具有一致的 ID 命名標準。  這讓程式設計者可以更容易的從其ID翻譯其類型和原點。  
  
-   強調某些類型的 ID 一對一的關聯性。  
  
-   依照廣泛使用 ID 姓名標準，為在 Windows 使用的 ID 命名。  
  
-   分割 ID 編號空間。  識別碼可由程式設計人員、MFC、視窗和 Visual C\+\+ 編輯之資源指派。  適當分割可協助避免 ID 編號重複。  
  
## ID 前置詞命名慣例  
 ID 的幾種類型的應用程式可能會發生。  ID 命名慣例的 MFC 定義不同的資源型別的不同的前置詞。  
  
 MFC 使用前置詞「IDR\_」表示適用於多個資源類型的資源 ID。  例如，針對指定的框架視窗， MFC 會使用相同的「IDR\_」前置詞表示功能表、快速鍵、字串和圖示資源。  下表顯示各種前置及其使用方式:  
  
|前置詞|用法|  
|---------|--------|  
|IDR\_|在多個資源類型 \(主要用於功能表、快速鍵和功能區\)。|  
|IDD\_|在對話方塊範本資源 \(例如， IDD\_DIALOG1\)。|  
|IDC\_|針對資料指標資源。|  
|IDI\_|對於圖示資源。|  
|IDB\_|針對點陣圖資源。|  
|IDS\_|針對字串資源|  
  
 在對話方塊資源中， MFC 會遵循下列慣例:  
  
|前置詞或標籤。|用法|  
|-------------|--------|  
|IDOK, IDCANCEL|針對標準按鈕 ID。|  
|IDC\_|對於其他對話方塊控制項。|  
  
 游標也使用「IDC\_」為前置詞。  因為一般的應用程式將有少量的資料指標和許多對話方塊控制項，命名衝突通常不是問題。  
  
 在選單資源中， MFC 會遵循下列慣例:  
  
|前置詞|用法|  
|---------|--------|  
|IDM\_|對於沒有使用 MFC 命令結構的功能表項目。|  
|ID\_|對於使用 MFC 命令結構的功能表命令。|  
  
 遵循 MFC 命令結構的命令必須有 `ON_COMMAND` 命令處理常式，而且有 `ON_UPDATE_COMMAND_UI` 處理常式。  如果這些命令處理常式追蹤的 MFC 命令結構，則它們會正常運作無論它們是否繫結至功能表命令、工具列按鈕或對話方塊列按鈕。  相同的「ID\_」前置詞為在程式的訊息列顯示的功能表提示字串也使用。  大部分在應用程式的功能表項目會遵循 MFC 命令慣例。  所有標準命令 ID \(例如， `ID_FILE_NEW`\) 遵循這個慣例。  
  
 MFC 也使用「IDP\_」，字串特定表單 \(而不是「IDS\_」\)。  以「IDP\_」為前置詞的字串是提示，也就是說，用於訊息方塊的字串。「IDP\_」字串可能包含「%1」和「%2」做為程式相依的字串預留位置。「IDP\_」字串通常有說明主題，而「IDS\_」字串沒有。「IDP\_」字串永遠當地語系化，而「IDS\_」字串可能不會當地化。  
  
 MFC 程式庫也使用「IDW\_」為前置詞，為特定的 ID 控制項表單 \(而不是「IDC\_」\)。  這些 ID 指派至例如檢視和分隔器由架構類別的子視窗。  MFC 實作 ID 前加上「AFX\_」作為前置詞。  
  
## ID 編號慣例  
 下表列出特定型別之 ID 的有效範圍。  某些限制為技術限制，其他的是設計來讓您的 ID 衝突視窗預先定義 ID 或 MFC 預設實作的慣例。  
  
 強烈建議您在建議的範圍內定義所有 ID。  因為沒有使用 0 ，所以這些範圍的下限是 1。  建議您使用通用慣例和使用 100 或 101 為第一個 ID.  
  
|前置詞|資源類型。|有效範圍|  
|---------|-----------|----------|  
|IDR\_|多個|1 個傳遞 0x6FFF|  
|IDD\_|對話方塊範本|1 個傳遞 0x6FFF|  
|IDC\_，IDI\_，IDB\_|游標，圖示，點陣圖|1 個傳遞 0x6FFF|  
|IDS\_， IDP\_|一般字串|1 個透過 0x7FFF|  
|ID\_|命令|0x8000 透過 0xDFFF|  
|IDC\_|控制項|8 個透過 0xDFFF|  
  
 範圍限制的原因:  
  
-   依照慣例，沒有使用 ID 值為 0。  
  
-   視窗實作條件限制為 true 的資源 ID 小於或等於 0x7FFF。  
  
-   MFC 的內部框架保留這些範圍:  
  
    -   0x7000 透過 0x7FFF \(請參閱\) afxres.h  
  
    -   0xE000 傳遞 0xEFFF \(請參閱\) afxres.h  
  
    -   16000 至 18000 \(請參閱\) afxribbonres.h  
  
     這些範圍在未來 MFC 實作可能會變更。  
  
-   幾個 Windows 系統命令來使用 0xF000 0xFFFF 的範圍。  
  
-   控制項 ID 1 至 7 為標準控制項有保留例如 IDOK 和 IDCANCEL。  
  
-   0x8000 範圍傳遞字串的 0xFFFF 為功能表提示是保留的輸入命令。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)