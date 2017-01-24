---
title: "方案 &lt;名稱&gt; 及其專案必須轉換成目前的格式。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 方案 &lt;名稱&gt; 及其專案必須轉換成目前的格式。
您開啟了在舊版 Visual Studio 中建立的方案。 方案和專案檔必須轉換成目前的格式，才能在您電腦上安裝的 Visual Studio 版本中開啟及編輯方案。 您可以選擇是否要立即轉換此方案。 格式轉換無法復原。  
  
> [!CAUTION]
>  如果此方案儲存在原始程式碼控制之下，而且您想要重新簽入已轉換的方案，請先判斷是否有其他方案共用該方案的任何專案。 如果有其他未轉換的方案正在使用此方案所包含的已轉換專案，請勿簽入此方案。 這會中斷這些方案的內部相依性，導致無法正常開啟或建置這些方案。  
  
 轉換前，您可能需要建立方案和專案檔的備份複本。  
  
> [!NOTE]
>  轉換 Visual Studio 方案時，舊的方案檔會以副檔名 ".old" 標示，並儲存在最上層方案目錄中。 轉換特定專案類型時 \(例如 Visual C\+\+ 專案\)，舊的專案檔同樣會以副檔名 ".old" 標示，並儲存在專案目錄中。  
  
 無法轉換唯讀專案。 只有具有編輯權限的使用者才能轉換這些專案。 您必須將已轉換方案的專案檔轉換成目前的格式，才能在方案中使用專案。 轉換方案或其任何專案之後，將無法再於舊版 Visual Studio 中編輯、建置或執行此方案。  
  
### 若要回應這個訊息  
  
1.  選取 \[是\] 或 \[否\]。  
  
    -   **是** \- 方案檔及其可編輯專案的檔案會轉換成您電腦上安裝之 Visual Studio 版本所使用的格式。 如果已轉換的方案儲存在原始程式碼控制之下，則會簽出至本機磁碟機，並開啟以供編輯。  
  
    -   **否** \- 方案及其專案不會轉換、不會從原始程式碼控制簽出，也不會開啟。  
  
 如果您隸屬於開發團隊，負責某個方案的所有人應該在其本機電腦上安裝相同版本的 Visual Studio。 為了確保方案和專案保持可供存取，請定期與您的團隊進行溝通。  
  
## 請參閱  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-tw/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)