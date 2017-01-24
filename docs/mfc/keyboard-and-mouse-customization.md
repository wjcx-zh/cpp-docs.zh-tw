---
title: "鍵盤和滑鼠自訂 | Microsoft Docs"
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
  - "自訂, 鍵盤和滑鼠 (MFC 擴充功能)"
  - "鍵盤和滑鼠自訂 (MFC 擴充功能)"
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 鍵盤和滑鼠自訂
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 可讓應用程式的使用者自訂如何處理鍵盤和滑鼠輸入。  使用者可以將鍵盤快速鍵自訂輸入至命令。  使用者可以選取要執行的命令或自訂滑鼠輸入，當使用者按兩下應用程式的特定視窗。  本主題說明如何自訂應用程式的項目。  
  
 在 \[**自訂**\] 對話方塊，使用者可以變更滑鼠和鍵盤的自訂控制項。  若要顯示這個對話方塊中，為 \[**自訂**\] 的使用者會在 \[**檢視**\] 功能表然後按一下 \[**工具列和停駐**\]。  在對話方塊中，使用者按一下 \[**鍵盤**\] 索引標籤或 \[**滑鼠**\] 索引標籤。  
  
## 鍵盤自訂  
 下圖顯示 \[**自訂**\] 對話方塊的 \[**鍵盤**\] 索引標籤。  
  
 ![&#91;自訂&#93; 對話方塊中的 &#91;鍵盤&#93; 索引標籤](../mfc/media/mfcnextkeyboardtab.png "MFCNextKeyboardTab")  
鍵盤自訂標籤  
  
 使用者以鍵盤選項指定一或多個鍵盤快速鍵加入至命令本身來互動。  在索引標籤的左側的清單上可用的命令。  使用者可以從功能表選取所有可用命令。  只有命令可以與鍵盤快速鍵關聯。  在使用者輸入新的快速鍵後， \[**指定**\] 按鈕會變成啟用。  當使用者按一下這個按鈕時，應用程式會與選取的命令與該捷徑相關聯。  
  
 所有在右欄中的清單方塊之目前指派鍵盤快速鍵清單。  使用者可以選取個別捷徑並移除或重設應用程式的所有對應。  
  
 如果您要支援在應用程式中使用此自訂，您必須建立 [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) 物件。  若要建立 `CKeyboardManager` 物件，呼叫 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md) 函式。  這個方法會建立並初始化鍵盤管理員。  如果您手動建立鍵盤管理員，您仍然必須呼叫 `CWinAppEx::InitKeyboardManager` 初始化。  
  
 如果您使用精靈來建立您的應用程式，精靈會使用鍵盤管理員。  在應用程式初始化鍵盤管理員後，架構會加入 \[**鍵盤**\] 索引標籤加入至 \[**自訂**\] 對話方塊。  
  
## 滑鼠自訂  
 下圖顯示 \[**自訂**\] 對話方塊的 \[**滑鼠**\] 索引標籤。  
  
 ![&#91;自訂&#93; 對話方塊中的 &#91;滑鼠&#93; 索引標籤](../mfc/media/mfcnextmousetab.png "MFCNextMouseTab")  
滑鼠自訂選項  
  
 使用者以這個選項將命令加入至按兩下滑鼠動作來互動。  使用者從視窗左側選取一個檢視然後使用右邊的控制項來命令與按兩下動作。  在使用者按一下 \[**關閉**\] 後，應用程式執行相關命令，每當使用者在檢視中任何位置按兩下。  
  
 根據預設，當您使用精靈建立應用程式時，滑鼠自訂未啟用。  
  
#### 啟用滑鼠自訂  
  
1.  透過呼叫 [CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md)初始化 [CMouseManager](../mfc/reference/cmousemanager-class.md) 物件。  
  
2.  使用 [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)，以取得指標給滑鼠管理員。  
  
3.  使用 [CMouseManager::AddView](../Topic/CMouseManager::AddView.md) 方法，加入檢視表滑鼠管理員。  這樣做要新增至滑鼠管理員的每個檢視。  
  
 在應用程式初始化之後滑鼠管理員，架構會將 \[**滑鼠**\] 索引標籤加入至 \[**自訂**\] 對話方塊。  如果您不會將任何檢視，存取這個選項將會導致未處理的例外狀況。  在您建立檢視清單後， \[**滑鼠**\] 選項可供使用者使用。  
  
 當您將新的檢視加入滑鼠管理員時，您會給它唯一 ID.  如果您要支援 Windows 的滑鼠自訂，您必須處理 `WM_LBUTTONDBLCLICK` 訊息和呼叫 [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) 函式。  當您呼叫這個函式時，其中一個參數是該視窗的 ID。  這是程式設計人員的責任記錄 ID 編號和物件相關聯的量值。  
  
## 安全性考量  
 如 [使用者定義類型](../mfc/user-defined-tools.md)中所述，使用者可以與使用者定義工具 ID 與按兩下事件關聯。  當使用者按兩下檢視時，應用程式會尋找符合關聯的 ID 的使用者工具  如果應用程式找到相符工具，它會執行工具。  如果應用程式找不到符合工具，將 ID 的 WM\_COMMAND 訊息至按兩下的檢視。  
  
 自訂的設定會儲存在登錄中。  透過編輯登錄，攻擊者可以用任意命令取代有效使用者工具 ID。  當使用者按兩下檢視時，這個檢視處理攻擊者個植的命令。  這可能會產生無法預期的潛在危險的行為。  
  
 此外，這種攻擊可能略過使用者介面保護。  例如，假設應用程式已停用的列印。  也就是在它的使用者介面， \[**列印**\] 功能表和按鈕無法使用。  通常這會防止應用程式列印。  但是，如果攻擊者編輯登錄，使用者可以直接透過按兩下檢視現在傳送列印命令，略過無法使用使用者介面項目。  
  
 為了防範這種攻擊，再執行之前，加入程式碼以驗證應用程式的命令處理常式的命令有效。  不要取決於使用者介面防止命令傳送到應用程式。  
  
## 請參閱  
 [MFC 自訂](../mfc/customization-for-mfc.md)   
 [CKeyboardManager Class](../mfc/reference/ckeyboardmanager-class.md)   
 [CMouseManager Class](../mfc/reference/cmousemanager-class.md)   
 [自訂的安全性影響](../mfc/security-implications-of-customization.md)